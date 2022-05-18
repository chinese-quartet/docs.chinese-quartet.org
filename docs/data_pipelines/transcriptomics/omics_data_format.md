## RNA-Seq

The data format that can be analysed online are pair-end FASTQ files, with suffixes of `_R1.fastq.gz` and `_R2.fastq.gz` or `_R1.fq.gz` and `_R2.fq.gz`.

Your dataset must contain four groups D5, D6, F7 and M8, with at least 2 technical replicates in each group. The reason is as follows.

1. In order to be able to compare with our reference dataset constructed based on the four groups D5, D6, F7 and M8, your dataset must contain D5, D6, F7 and M8.

2. The SNR is calculated based on the ratio of signal (between the four groups) to noise (technical replicates within the group), so each group contains at least two technical replicates.

!!! note 
    In addition, there is one thing to note when using the Quartet RNAseq APP. The "Sample ID" in the parameter setting page refers to the number of samples. 

    For example, if your data contains 8 samples(such as D5, D6, F7 and M8 * 2 technical replicates), you should fill in "8".

## miRNAseq
We haven't developed the analysis pipeline.