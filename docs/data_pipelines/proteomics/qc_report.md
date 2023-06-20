From Quantified Expression Profiles to QC Report

!!! note 
    You can find the source code on [chinese-quartet/quartet-protqc-report](https://github.com/chinese-quartet/quartet-protqc-report.git)

## I. Prepare data & metadata files

### Data File

The data file provides the quantified proteins that are mapped to gene symbols and quantified peptide sequences, and the missing values are allowed. The required file format has the columns named *Type* and *Feature*. 
> Please ensure that there are **no duplicated** column names in the data file.

> If the type of features is **Gene Symbol** only, then the metric ***Relative Correlation with Reference Datasets (RC)*** will not be calculated.

Please see the example of the required data file as follows.

- [Data Template](../../assets/templates/proteomics_pipeline_data_template.csv)

### Metadata File

The metadata file has the information of each sample ID in the data file. With columns named "library", "sample" (D5, D6, F7 and M8 for Quartet samples). 
> Remember that the column "library" and column names of the data file table must be in one-to-one correspondence.

> If the sample type **"D6"** is missing, then the metric ***Relative Correlation with Reference Datasets (RC)*** will not be calculated.

Please see the example of the required data file as follows.

- [Metadata Template](../../assets/templates/proteomics_pipeline_meta_template.csv)

## II. Step by Step Guide

### To analyze your data on Quartet Data Portal

See details on [Step by Step Guide](../../getting_started/step_by_step_guide_protein.md)

### To analyze your data on your own server

1. Pull docker image 

    More versions on [Docker Registry](https://github.com/chinese-quartet/quartet-protqc-report/pkgs/container/quartet-protqc-report)

    ```
    docker pull ghcr.io/chinese-quartet/quartet-protqc-report:v0.2.4-6534a16b
    ```

2. Run quartet-protqc-report with docker image

    Assuming that your data file is named `data.csv` and metadata file is named `metadata.csv` and all files are placed in `/your-dir` directory.

    ```
    docker run -v /your-dir:/data -it ghcr.io/chinese-quartet/quartet-protqc-report:v0.2.4-6534a16b -d /data/data.csv -m /data/metadata.csv -o /data
    ```

3. Find your QC report in `/your-dir/multiqc_report.html`

## III. QC metrics

The package protqc output Quality Control(QC) results of proteomics data for Quartet Project. The QC pipeline starts from the expression profiles at peptide/protein levels, and enables to calculate 6 metrics. A Total score is the geometric mean of the linearly normalized values of these metrics.

1. ***Number of features***: We expect as many proteins (mapped to gene symbols) as possible for downstreaming analyses. Identified proteins were filtered by the rule of 5% FDR. However, if you set stricter rules (e.g., 1% FDR), less number but high confidence of proteins will be retained (then your data may rank relatively low in terms of *Number of features*).

2. ***Missing percentage (%)***: Too many missing values interfere with comparability. This metric is calculated globally.

3. ***Coefficient of variantion (CV, %)***: A CV value is calculated to indicate the dispersion within replicates feature by feature.

4. ***Absolute Correlation***: Pearson correlation reflects overall reproducibility within replicates. We calculate correlation coefficients between each two replicates within each biological sample (D5, D6, F7, M8), and take the median as the final value for absolute correlation.

5. ***Signal-to-Noise Ratio (SNR)***: SNR is established to characterize the ability of a platform or lab or batch, which is able to distinguish intrinsic differences among distinct biological sample groups (“signal”) from variations in technical replicates of the same sample group ("noise").

6. ***Relative Correlation with Reference Datasets (RC)***: RC is used for assessment of quantitative consistency with the reference dataset at relative levels. For shotgun proteomics, quantitation at peptide levels is theoretically more reliable. Therefore, the reference dataset is established by benchmarking the relative expression values (log2FCs), for each peptide sequence of each sample pair (D5/D6, F7/D6, M8/D6), in historical datasets at peptide levels. We calculate relatively qualified (satisfied with thresholds of p < 0.05) log2FCs of the queried data, for overlapped peptides with the reference dataset, as the input for the assessment of quantitative consistency. Then RC value is Pearson correlation coefficient between the test dataset and the reference dataset.
