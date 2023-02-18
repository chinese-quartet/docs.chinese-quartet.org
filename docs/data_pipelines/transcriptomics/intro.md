## Requirements for your data and metadata
- [`Metadata Template` - Download the metadata template and prepare your metabata](./metadata_template.md)
- [`Data Format` - Follow the data format requirements to prepare your genomics data](./omics_data_format.md)

## Analyze your data on Quartet Data Portal

See more details on [Step by Step Guide](../../getting_started/step_by_step_guide_rna.md)

## Analyze your data on your own server

Quartet RSeQC Report is a quality assessment tool for RNA-seq data. It contains two subcommands: `workflow` and `report`. The workflow command takes raw reads (in FASTQ format), produces a set of qc result files from them (More details on [RNA-Seq QC for Quartet](./analysis_pipeline.md)). and you can use `report` command to report the results finally (More details on [QC Report for Quartet RNA-Seq](./qc_report.md)).

Assuming your data files are in the /your-dir directory.

0. Prepare a set of subdirectories

    ```
    mkdir -p /your-dir/fastq_screen /your-dir/hisat2 /your-dir/gtf /your-dir/results /your-dir/raw-data /your-dir/report
    ```

1. Download the dependency files

    ```
    # 1. Download reference genomes for `fastq_screen` (More details on https://figshare.com/articles/online_resource/fastq_screen_zip/22121078)
    wget https://figshare.com/ndownloader/files/39310673 -O /your-dir/fastq_screen/fastq_screen.zip
    unzip /your-dir/fastq_screen/fastq_screen.zip -d /your-dir/fastq_screen

    # 2. Download GTF file (More details on https://figshare.com/articles/online_resource/Homo_sapiens_GRCh38_93_gtf/22117475)
    wget https://figshare.com/ndownloader/files/39308702 -O /your-dir/gtf/Homo_sapiens.GRCh38.93.gtf

    # 3. Download Hisat2 index files (More details on https://figshare.com/articles/online_resource/hisat2_zip/22120538)
    wget https://figshare.com/ndownloader/files/39310418 -O /your-dir/hisat2/hisat2.zip
    unzip /your-dir/hisat2/hisat2.zip -d /your-dir/hisat2
    ```

2. Place your data files into `/your-dir/raw-data` directory

3. Pull docker image 

    More versions on [Docker Registry](https://github.com/chinese-quartet/quartet-rseqc-report/pkgs/container/quartet-rseqc-report)

    ```
    docker pull ghcr.io/chinese-quartet/quartet-rseqc-report:v0.2.3-31f4ef89
    ```

4. Generate qc result files by workflow command

    ```
    docker run -d -v /your-dir:/data -it ghcr.io/chinese-quartet/quartet-rseqc-report:v0.2.3-31f4ef89 workflow -i /data/hisat2 -g /data/gtf/gencode.v36.annotation.gtf -s /data/fastq_screen/fastq_screen.conf --output-dir /data/results --r1 /data/raw-data/example_R1.fq.gz --r2 /data/raw-data/example_R2.fq.gz
    ```

5. Report the results

    ```
    docker run -d -v /your-dir:/data -it ghcr.io/chinese-quartet/quartet-rseqc-report:v0.2.3-31f4ef89 report -d /data/results -m /data/metadata.csv --output-dir /data/report
    ```

6. Find your QC report in `/your-dir/multiqc_report.html`
