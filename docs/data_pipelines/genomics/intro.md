## Chinese Quartet DNA reference materials

With the rapid development of sequencing technology and the dramatic decrease of sequencing costs, DNA sequencing has been widely used in scientific research, diagnosis of and treatment selection for human diseases. However, due to the lack of effective quality assessment and control of the high-throughput omics data generation and analysis processes, variants calling results are seriously inconsistent among different technical replicates, batches, laboratories, sequencing platforms, and analysis pipelines, resulting in irreproducible scientific results and conclusions, huge waste of resources, and even endangering the life and health of patients. Therefore, reference materials for quality control of the whole process from omics data generation to data analysis are urgently needed. 

We first established genomic DNA reference materials from four immortalized B-lymphoblastoid cell lines of a Chinese Quartet family including parents and monozygotic twin daughters to make performance assessment of germline variants calling results. To establish small variant benchmark calls and regions, we generated whole-genome sequencing data in nine batches, with depth ranging from 30x to 60x, by employing PCR-free and PCR libraries on four popular short-read sequencing platforms (Illumina HiSeq XTen, Illumina NovaSeq, MGISEQ-2000, and DNBSEQ-T7) with three replicates at each batch, resulting in 108 libraries in total and 27 libraries for each Quartet DNA reference material. Then, we selected variants concordant in multiple call sets and in Mendelian consistency within Quartet family members as small variant benchmark calls, resulting in 4.2 million high-confidence variants (SNV and Indel) and 2.66 G high confidence genomic region, covering 87.8% of the human reference genome (GRCh38, chr1-22 and X). Two orthogonal technologies were used for verifying the high-confidence variants. The consistency rate with PMRA (Axiom Precision Medicine Research Array) was 99.6%, and 95.9% of high-confidence variants were validated by 10X Genomics whole-genome sequencing data. Genetic built-in truth of the Quartet family design is another kind of “truth” within the four Quartet samples. Apart from comparison with benchmark calls in the benchmark regions to identify false-positive and false-negative variants, pedigree information among the Quartet DNA reference materials, i.e., reproducibility rate of variants between the twins and Mendelian concordance rate among family members, are complementary approaches to comprehensively estimate genome-wide variants calling performance. Finally, we developed a whole-genome sequencing data quality assessment pipeline and demonstrated its utilities with two examples of using the Quartet reference materials and datasets to evaluate data generation performance in three sequencing labs and different data analysis pipelines.

## Requirements for your data and metadata
- [`Metadata Template` - Download the metadata template and prepare your metabata](./metadata_template.md)
- [`Data Format` - Follow the data format requirements to prepare your genomics data](./omics_data_format.md)

## Analyze your data on Quartet Data Portal

See more details on [Step by Step Guide](../../getting_started/step_by_step_guide_dna.md)

## Analyze your data on your own server

Quartet DSeQC Report is a quality assessment tool for WGS/WES data. It supports two format: `Fastq` and `vcf`. And it contains three subcommands: `fq-workflow`, `vcf-workflow` and `report`. The `fq-workflow` command takes raw reads (in FASTQ format), produces a set of qc result files from them (More details on [DNA-Seq (WGS) QC for Quartet](./analysis_pipeline_wgs.md) and [DNA-Seq (WES) QC for Quartet](./analysis_pipeline_wes.md)).

When you have produced vcf files from your own pipeline, you can use the `vcf-workflow` command. It takes vcf files and produces a set of qc result files from them. 

After above processes, you can use `report` command to report the results finally (More details on [QC Report for Quartet RNA-Seq](./qc_report.md)).

### If you have raw reads (in FASTQ format)

!!! note annotate "CAUTION"
    The pipeline for raw reads depends on Sentieon software. So if you want to use the pipeline, you need to specify the license server by `-S` option. 
    
    If you don't have the license, we recommend you analyze your data on [Quartet Data Portal](https://chinese-quartet.org). If not, please contact [Sentieon](https://www.sentieon.com/) or use the vcf mode.

    If you have your own pipeline, you can use your own pipeline to produce vcf files from your raw reads. Then you can use the `vcf-workflow` command to analyze your data. More details at the following section.

    <b>[STATEMENT: We don't have any relationship with Sentieon and don't get any benefit from Sentieon.]</b>

Assuming your data files are in the /your-dir directory.

0. Prepare a set of subdirectories

    ```
    mkdir -p /your-dir/raw-data /your-dir/references /your-dir/results /your-dir/report
    ```

1. Download the dependency files

    ```
    wget https://zenodo.org/record/7800049/files/quartet-dseqc-report-reference-data-v20230404.zip?download=1

    unzip quartet-dseqc-report-reference-data-v20230404.zip

    # You need to place the reference files into /your-dir/references directory
    ```

2. Place your data files into `/your-dir/raw-data` directory

3. Pull docker image 

    More versions on [Docker Registry](https://github.com/chinese-quartet/quartet-rseqc-report/pkgs/container/quartet-dseqc-report)

    ```
    docker pull ghcr.io/chinese-quartet/quartet-dseqc-report:v0.2.3-fc1077eb
    ```

4. Generate qc result files by workflow command

    ```
    # For WGS Fastq data
    ## Assume the following conditions:
    ### 1. Your file name is like: d5.R1.gz, d5.R2.gz, d6.R1.gz, d6.R2.gz, f7.R1.gz, f7.R2.gz, m8.R1.gz, m8.R2.gz
    ### 2. All of your reference files are in the /your-dir/references directory, including reference_datasets_v202103, GRCh38.d1.vd1 and fastq_screen_reference directories. [You can follow the step 1 to download the reference files.]
    ### 3. If your data is produced by BGI sequencing platform, you can use -p BGI to set the platform. otherwise -p ILLUMINA
    ### 4. The pipeline depends on Sentieon software, you need to specify -S to set the license server.
    ### 5. The output directory is /your-dir/results

    docker run -d -v /your-dir:/data -it ghcr.io/chinese-quartet/quartet-dseqc-report:v0.2.3-fc1077eb fq-workflow --d5-r1 /data/raw-data/d5.R1.gz --d5-r2 /data/raw-data/d5.R2.gz --d6-r1 /data/raw-data/d6.R1.gz --d6-r2 /data/raw-data/d6.R2.gz --f7-r1 /data/raw-data/f7.R1.gz --f7-r2 /data/raw-data/f7.R2.gz --m8-r1 /data/raw-data/m8.R1.gz --m8-r2 /data/raw-data/m8.R2.gz -p BGI -B /data/references/reference_datasets_v202103 -R /data/references/GRCh38.d1.vd1 -F /data/references/fastq_screen_reference -S 192.168.1.1:8990 --output-dir /data/results

    # For WES Fastq data
    ## Assume the following conditions:
    ### 1. Your file name is like: d5.R1.gz, d5.R2.gz, d6.R1.gz, d6.R2.gz, f7.R1.gz, f7.R2.gz, m8.R1.gz, m8.R2.gz
    ### 2. All of your reference files are in the /your-dir/references directory, including reference_datasets_v202103, GRCh38.d1.vd1 and fastq_screen_reference directories. [You can follow the step 1 to download the reference files.]
    ### 3. If your data is produced by BGI sequencing platform, you can use -p BGI to set the platform. otherwise -p ILLUMINA
    ### 4. The pipeline depends on Sentieon software, you need to specify -S to set the license server.
    ### 5. You need to prepare your bed file and set -b option.
    ### 6. The output directory is /your-dir/results

    docker run -d -v /your-dir:/data -it ghcr.io/chinese-quartet/quartet-dseqc-report:v0.2.3-fc1077eb fq-workflow --d5-r1 /data/raw-data/d5.R1.gz --d5-r2 /data/raw-data/d5.R2.gz --d6-r1 /data/raw-data/d6.R1.gz --d6-r2 /data/raw-data/d6.R2.gz --f7-r1 /data/raw-data/f7.R1.gz --f7-r2 /data/raw-data/f7.R2.gz --m8-r1 /data/raw-data/m8.R1.gz --m8-r2 /data/raw-data/m8.R2.gz -p BGI -B /data/references/reference_datasets_v202103 -R /data/references/GRCh38.d1.vd1 -F /data/references/fastq_screen_reference -S 192.168.1.1:8990 --bed-file /data/references/your-bed-file --output-dir /data/results
    ```

5. Report the results

    ```
    docker run -d -v /your-dir:/data -it ghcr.io/chinese-quartet/quartet-dseqc-report:v0.2.3-fc1077eb report -d /data/results --output-dir /data/report
    ```

6. Find your QC report in `/your-dir/report/multiqc_report.html`

### If you have vcf files

Assuming your data files are in the /your-dir directory.

0. Prepare a set of subdirectories

    ```
    mkdir -p /your-dir/raw-data /your-dir/references /your-dir/results /your-dir/report
    ```

1. Download the dependency files

    ```
    wget https://zenodo.org/record/7800049/files/quartet-dseqc-report-reference-data-v20230404.zip?download=1

    unzip quartet-dseqc-report-reference-data-v20230404.zip

    # You need to place the reference files into /your-dir/references directory
    ```

2. Place your data files into `/your-dir/raw-data` directory

3. Pull docker image 

    More versions on [Docker Registry](https://github.com/chinese-quartet/quartet-rseqc-report/pkgs/container/quartet-dseqc-report)

    ```
    docker pull ghcr.io/chinese-quartet/quartet-dseqc-report:v0.2.3-fc1077eb
    ```

4. Generate qc result files by workflow command

    ```
    # For WGS data
    ## Assume the following conditions:
    ### 1. All of your reference files are in the /your-dir/references directory, including reference_datasets_v202103 and GRCh38.d1.vd1 directories. [You can follow the step 1 to download the reference files.]
    ### 2. If your data is produced by BGI sequencing platform, you can use -p BGI to set the platform. otherwise -p ILLUMINA
    ### 3. The output directory is /your-dir/results

    docker run -d -v /your-dir:/data -it ghcr.io/chinese-quartet/quartet-dseqc-report:v0.2.3-fc1077eb vcf-workflow --vcf-d5 /data/raw-data/d5.vcf --vcf-d6 /data/raw-data/d6.vcf --vcf-f7 /data/raw-data/f7.vcf --vcf-m8 /data/raw-data/m8.vcf -p BGI -B /data/references/reference_datasets_v202103 -R /data/references/GRCh38.d1.vd1 --output-dir /data/results

    # For WES data
    ## Assume the following conditions:
    ### 1. All of your reference files are in the /your-dir/references directory, including reference_datasets_v202103 and GRCh38.d1.vd1 directories. [You can follow the step 1 to download the reference files.]
    ### 2. If your data is produced by BGI sequencing platform, you can use -p BGI to set the platform. otherwise -p ILLUMINA
    ### 3. You need to prepare your bed file and set -b option.
    ### 4. The output directory is /your-dir/results

    docker run -d -v /your-dir:/data -it ghcr.io/chinese-quartet/quartet-dseqc-report:v0.2.3-fc1077eb vcf-workflow --vcf-d5 /data/raw-data/d5.vcf --vcf-d6 /data/raw-data/d6.vcf --vcf-f7 /data/raw-data/f7.vcf --vcf-m8 /data/raw-data/m8.vcf -p BGI -B /data/references/reference_datasets_v202103 -R /data/references/GRCh38.d1.vd1 --bed-file /data/references/your-bed-file --output-dir /data/results
    ```

5. Report the results

    ```
    docker run -d -v /your-dir:/data -it ghcr.io/chinese-quartet/quartet-dseqc-report:v0.2.3-fc1077eb report -d /data/results --output-dir /data/report

    # Known issue:
    # Only support one uuid directory in /your-dir/results directory.
    # If you have multiple uuid directories in /your-dir/results directory, the report will be failed or messy.
    # We will fix this issue in the future.
    ```

6. Find your QC report in `/your-dir/report/multiqc_report.html`

## More details about the analysis pipeline
- [`QC APP` - WGS QC for Quartet](./analysis_pipeline_wgs.md)
- [`QC APP` - WES QC for Quartet](./analysis_pipeline_wes.md)
