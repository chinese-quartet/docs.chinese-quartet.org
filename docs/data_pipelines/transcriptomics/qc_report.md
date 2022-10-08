## Quality Metrics

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


### Quality Metrics

| Quality Metrics                           | Category    | Description                                                                                                                                                                                                                                                 | Reference Value |
| ----------------------------------------- | ----------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------- |
| Number of detected genes                  | One group   | This metric is used to estimate the  detection abundance of one sample.                                                                                                                                                                                     | (**, 58,395]    |
| Detection Jaccard index (JI)              | One group   | Detection JI is the ratio of number of the  genes detected in both replicates than the number of the genes detected in  either of the replicates. This metric is used to estimate the  repeatability of one sample detected gene from different replicates. | [0.8, 1]        |
| Coefficient of variation (CV)             | One group   | CV is calculated based on the  normalized expression levels in all 3 replicates of one sample for each  genes. This metric is used to estimate the repeatability of one sample  expression level from different replicates.                                 | [0, 0.2]        |
| Correlation of technical replicates (CTR) | One group   | CTR is calculated based on the correlation  of one sample expression level from different replicates.                                                                                                                                                       | [0.95, 1]       |
| Signal-to-noise Ratio (SNR)               | More groups | Signal is defined as the average distance  between libraries from the different samples on PCA plots and noise are those  form the same samples. SNR is used to assess the ability to distinguish  technical replicates from different biological samples.  | [5, inf)        |
| Sensitivity of  detection                 | One group   | Sensitivity is the proportion of  "true" detected genes from reference dataset which can be  correctly detected by the test set.                                                                                                                            | [0.96, 1]       |
| Specificity of  detection                 | One group   | Specificity is the proportion of  "true" non-detected genes from reference dataset which can be  correctly not detected by the test set.                                                                                                                    | [0.94, 1]       |
| Consistency  ratio of relative expression | Two groups  | Proportion of genes that falls into  reference range (mean ± 2 fold SD) in relative ratio (log2FC).                                                                                                                                                         | [0.82, 1]       |
| Correlation of  relative log2FC           | Two groups  | Pearson correlation between mean value  of reference relative ratio and test site.                                                                                                                                                                          | [0.96,1]        |
| Sensitivity of  DEGs                      | Two groups  | Sensitivity is the proportion of  "true" DEGs from reference dataset which can be correctly  identified as DEG by the test set.                                                                                                                             | [0.80, 1]       |
| Specificity of  DEGs                      | Two groups  | Specificity is the proportion of  "true" not DEGs from reference dataset which can be can be  correctly identified as non-DEG by the test set.                                                                                                              | [0.95, 1]       |
