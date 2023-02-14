## Genomics
For whole-genome sequencing, the quality assessment is started from FASTQ files and can be divided into three parts: pre-alignment quality assessment, post-alignment assessment, and small variants calling results assessment. The quality of pre-alignment is assessed by FastQC and FastQ Screen, while post-alignment is assessed by Qualimap. The performance of variants calling results are evaluated by reference datasets and Quartet family-dependent built-in genetic truth. MultiQC was used for compiling QC results together. Pre-alignment and Post-alignment quality assessment are not available if user start from VCF files.

## Transcriptomics
For RNA-seq, the quality assessment is started from FASTQ files and can be divided into three parts: pre-alignment, post-alignment, and gene-expression profiles. The quality of pre-alignment is assessed by FastQC and FastQ Screen, while post-alignment is assessed by Qualimap, while the quality control of gene expression profiles is based on the Quartet reference datasets and the internal information of each batch itself. MultiQC was used for compiling QC results together.

## Proteomics

For proteomics, the quality assessment is started from expression profiles formatted as .csv files, and the pipeline is implemented into QC Report module. It is based on built-in biological differences of the samples and consistency with the reference dataset at relative quantitation levels. The former is scored as an Signal-to-Noise Ratio (SNR) and displayed in a PCA scatterplot, and the latter is scored as Pearson correlation to the reference dataset and displayed in a scatterplot, in which a strict filter criteria was applied (features with p.adj<0.05 in at least 4 batches were kept). MultiQC was used for compiling QC results together.

## Metabolomics

Quality Assessment of a Quartet metabolic profiling dataset is based on built-in biological differences of the samples, consistency with the reference dataset at relative quantitation levels. The three QC metrics, including Signal-to-Noise Ratio (SNR), Relative Correlation with Reference Datasets (RC), and Recall of DAMs in Reference Datasets (Recall), to comprehensively assess the performance of metabolic profiles from 2 aspects: reproducibility and accuracy.
