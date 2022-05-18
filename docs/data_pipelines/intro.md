## Genomics
For whole-genome sequencing, the quality assessment is started from FASTQ files and can be divided into three parts: pre-alignment quality assessment, post-alignment assessment, and small variants calling results assessment. The quality of pre-alignment is assessed by FastQC and FastQ Screen, while post-alignment is assessed by Qualimap. The performance of variants calling results are evaluated by reference datasets and Quartet family-dependent built-in genetic truth. MultiQC was used for compiling QC results together. Pre-alignment and Post-alignment quality assessment are not available if user start from VCF files.

## Transcriptomics
For RNA-seq, the quality assessment is started from FASTQ files and can be divided into three parts: pre-alignment, post-alignment, and gene-expression profiles. The quality of pre-alignment is assessed by FastQC and FastQ Screen, while post-alignment is assessed by Qualimap, while the quality control of gene expression profiles is based on the Quartet reference datasets and the internal information of each batch itself. MultiQC was used for compiling QC results together.

## Proteomics

Comming soon...

## Metabolomics

Comming soon...