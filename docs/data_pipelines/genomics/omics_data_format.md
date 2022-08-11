## Omics Data Format

The data format that can be analysed online are:

- pair-end FASTQ files, with suffixes of  `_LCL5.R1.fastq.gz` and `_LCL5.R2.fastq.gz`. The file naming rules for LCL6, LCL7, LCL8 are the same as above

- unzipped VCF files, with suffixes of `.vcf`.

!!! note 
    In addition, there is one thing to note when using the Quartet DNAseq APP. The "Sample ID" in the parameter setting page refers to the number of data sets (one technical replicate of each sample is considered as one set, i.e. D5-D6-F7-M8).
    
    For example, if you provide data for 8 samples, that means two sets of data, so fill in "2".