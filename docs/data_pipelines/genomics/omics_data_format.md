## Omics Data Format

The data format that can be analyzed online are:

- Pair-end FASTQ files, with suffixes of _R1.fastq.gz and _R2.fastq.gz or _R1.fq.gz and _R2.fq.gz.

- unzipped VCF files, with suffixes of `.vcf`.

We suggest to standardize the file names of updated data files as follows:

**Quartet_Omics_SequencePlatform_SequenceMachine_LibraryPrep_SequenceSite_Sample_Replicate_Date_R1/R2.fastq/fq.gz**

(1) Omics

| Omics type  | Character |
| :---------- | :-------- |
| DNA WGS     | WGS       |
| DNA WES     | WES       |

(2) SequencePlatform

| Platform    | Character |
| :---------- | :-------- |
| illumina    | ILM       |
| BGI         | BGI       |
| Pacbio      | Pacbio    |
| Nanopore    | ONT       |

Please note that the tables provides examples of commonly used representative sequencing platforms, rather than an exhaustive compilation of all exiting sequencing platforms. If you use sequencing platforms not listed in the table, please use 2 to 6 letters as abbreviations to represent the sequencing platforms.

(3) SequenceMachine

| Platform    | Machine       | Character  |
|:----------- | :-------------| :----------|
| illumina    | XTen          | XTen       |
| illumina    | Novasq        | Nova       |
| illumina    | Hiseq4000     | Hiseq4000  |
| illumina    | Hiseq2500     | Hiseq2500  |
| illumina    | 10x           | 10x        |
| BGI         | SEQ500        | SEQ500     |
| BGI         | SEQ2000       | SEQ2000    |
| BGI         | DNBSEQ-T7     | T7         |
| Pacbio      | Sequel        | Sequel     |
| Pacbio      | Sequel II     | Sequel2    |
| Nanopore    | PromethION 24 | P24        |
| Nanopore    | MinION        | MinION     |

Please note that the tables provides examples of commonly used representative sequencing machines, rather than an exhaustive compilation of all exiting sequencing machines. If you use sequencing platforms not listed in the table, please use 2 to 6 letters as abbreviations to represent the sequencing machines.

(4) LibraryPrep

| LibraryPrep | Character     |
|:----------- | :-------------|
| PCR         | PCR           |
| PCR-free    | PCRfree       |

(5) SequenceSite

Please use a few uppercase letters as abbreviations to represent the sequence centers or labs. For example, Fudan to FD.

(6) Sample

| Sample      | Character |
| :---------- | :-------- |
| Quartet-D5  | D5        |
| Quartet-D6  | D6        |
| Quartet-F7  | F7        |
| Quartet-M8  | M8        |

(7) Replicate
If you sequenced multiple replicates for the same reference material, use numbers such as 1, 2, 3, ... to represent technical replicates.

(8) Date
The format of Date is yyyymmdd. For example, June 25, 2023 shoud be written to 20230625.

Here are some examples of file names:

Fastq read 1: **Quartet_WGS_ILM_Nova_PCRfree_FD_D5_1_20230635_R1.fq.gz**

Fastq read 2: **Quartet_WGS_ILM_Nova_PCRfree_FD_D5_2_20230635_R2.fq.gz**


!!! note 
    In addition, there is one thing to note when using the Quartet DNAseq APP. The "Sample ID" in the parameter setting page refers to the number of data sets (one technical replicate of each sample is considered as one set, i.e. D5-D6-F7-M8).
    
    For example, if you provide data for 8 samples, that means two sets of data, so fill in "2".
