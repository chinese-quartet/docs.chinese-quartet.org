### Quality Metrics

|Metric|Description|Range v1|Cutoff v1|
|-----|--------|--------|---------|
|Signal-to-Noise Ratio (SNR)|Based on the Quartet design, a Signal-to-Noise Ratio (SNR) metric was established to gauge the performance of a platform, a lab, a protocol, or a batch in distinguishing the intrinsic biological differences (“signal”) among the Quartet samples from variations among technical replicates of the same sample group (“noise”). Generally, a lower SNR value indicates lower discriminating power, vice versa. For an SNR value around or below zero, it means that the magnitude of signal is at a similar level as the noise or even lower than the noise. In this case, it is almost impossible to distinguish different sample groups under the high level of technical noises. Here, we used the first two principal components for calculating SNR, in correspondence with visualization in commonly used two-dimensional PCA plots.|(-∞, +∞)|>12 |
|Relative correlation with reference datasets (RC)|Relative correlation with reference datasets was calculated based on the Pearson correlation coefficient between the ratio-based expression levels of a dataset for a given pair of groups and the corresponding ratio-based reference datasets, representing the trend of numerical consistency of the ratio-based expression profiles. Reference datasets were pre-defined datasets in the format of a geometric mean by summarizing from the fold-changes calculated from the high-quality RNAseq datasets, providing “ground truth” for benchmarking.|[-1, 1] |>0.89    |
|MCC|MCC is a widely used statistic in the field of bioinformatics and machine learning, which combines test sensitivity and specificity. In this study, we used MCC to measure the consistency of DEGs detected from a dataset for a given pair of samples with those from the reference DEGs, or “MCC of DEGs”. Reference DEGs and non-DEGs as true positive and true negative sets were integrated by consensus voting. When DEGs and non-DEGs of a given dataset were identified, the number of True Positive (TP), True Negative (TN), False Positive (FP) and False Negative (FN) could be calculated. MCC is then computed.|[-1, 1]|>0.54|
|Total score|The total performance score is calculated to measure the overall quality of a dataset generated from a lab for its effectiveness in quantifying the transcriptomic differences among the four Quartet RNA reference materials by summarizing reference dataset-independent quality measurement (SNR) and reference dataset-dependent quality measurement (RC). The total score is expressed as the geometrical mean of SNR and RC.|(-∞, +∞)| |


### Raw Data Quality & Mapping Quality

| Quality Metrics                  | Software     | Description | Reference Value |
| -------------------------------- | ------------ | ----------- | --------------- |
| Total.Sequences                  | Fastqc       | -           | > 10 M          |
| GC_beforemapping                 | Fastqc       | -           | 40% - 60%       |
| total_deduplicated_percentage    | Fastqc       | -           |                 |
| Human.percentage                 | FastQ Screen | -           | > 90 %          |
| ERCC.percentage                  | FastQ Screen | -           | < 5%            |
| EColi.percentage                 | FastQ Screen | -           | < 5%            |
| Adapter.percentage               | FastQ Screen | -           | < 5%            |
| Vector.percentage                | FastQ Screen | -           | < 5%            |
| rRNA.percentage                  | FastQ Screen | -           | < 10%           |
| Virus.percentage                 | FastQ Screen | -           | < 5%            |
| Yeast.percentage                 | FastQ Screen | -           | < 5%            |
| Mitoch.percentage                | FastQ Screen | -           | < 5%            |
| Phix.percentage                  | FastQ Screen | -           | < 5%            |
| No.hits.percentage               | FastQ Screen | -           | < 5%            |
| percentage_aligned_beforemapping | Qualimap     | -           | > 90%           |
| error_rate                       | Qualimap     | -           | < 5%            |
| bias_53                          | Qualimap     | -           |                 |
| GC_aftermapping                  | Qualimap     | -           | 40% - 60%       |
| percent_duplicates               | Qualimap     | -           |                 |
| sequence_length                  | Qualimap     | -           | ~150            |
| median_insert_size               | Qualimap     | -           | 200 - 300       |
| mean_coverage                    | Qualimap     | -           |                 |
| ins_size_median                  | Qualimap     | -           | 200 - 300       |
| ins_size_peak                    | Qualimap     | -           | 200 - 300       |
| exonic                           | Qualimap     | -           | 40% - 60%       |
| intronic                         | Qualimap     | -           | 40% - 60%       |
| intergenic                       | Qualimap     | -           | < 10%           |
