<h2 align="center">Docs for Quartet Data Portal</h2>
<p align="center">Quality Control and Data Integration of Multi-omics Profiling</p>

<p align="center">
<img src="https://img.shields.io/github/license/chinese-quartet/docs.chinese-quartet.org.svg?label=License" alt="License"> 
<a href="https://github.com/chinese-quartet/docs.chinese-quartet.org/releases"><img alt="Latest Release" src="https://img.shields.io/github/release/chinese-quartet/docs.chinese-quartet.org.svg?label=Latest%20Release"/></a>
<a href="https://github.com/chinese-quartet/docs.chinese-quartet.org/actions/workflows/publish-docs.yml"><img alt="Quality Control" src="https://github.com/chinese-quartet/docs.chinese-quartet.org/actions/workflows/publish-docs.yml/badge.svg"/></a>
</p>

Multi-omics (or molecular phenomics) profiling at the genomic, transcriptomic, proteomic, and metabolomic levels is the cornerstone of high-throughput technologies for discovering biomarkers for precision medicine. However, the lack of quality control procedures of multi-omics profiling during data generation and data analysis can lead to false findings, raising serious concerns about the reliability of multi-omics studies.

The Quartet Project provides publicly accessible multi-omics reference materials and practical tools to enhance the reproducibility and reliability of multi-omics results. Well-characterized multiomics reference materials and quality control metrics pertinent to precision medicine study purposes can be used to measure and mitigate technical variation, enabling more accurate cross-batch and cross-omics data integration in increasingly large-scale and longitudinal studies such as the International Human Phenome Project.

## For Developers

### Install Dependencies

```
# Clone the repository
git clone https://github.com/yjcyxky/docs.chinese-quartet.org.git

cd docs.chinese-quartet.org

# Create virtual environment
virtualenv .env

# Activate virtual environment
source .env/bin/activate

# Install dependencies
pip install -r requirements.txt
```

### Launch Docs Website

If you want to launch the docs website locally, you can use the following command:

```
mkdocs serve
```

The output should be like this:

```
(quartet-docs) ➜ /quartet-docs git:(master) ✗ > mkdocs serve
INFO     -  Building documentation...
WARNING  -  Config value: 'announce'. Warning: Unrecognised configuration name: announce
WARNING  -  Config value: 'announce_text'. Warning: Unrecognised configuration name: announce_text
INFO     -  Cleaning site directory
INFO     -  The following pages exist in the docs directory, but are not included in the "nav" configuration:
              - about/collaborators.md
              - about/members.md
              - data_dictionary/about.md
              - data_dictionary/metadata.md
              - ...
INFO     -  Documentation built in 3.18 seconds
INFO     -  [09:30:55] Watching paths for changes: 'docs', 'mkdocs.yml'
INFO     -  [09:30:55] Serving on http://127.0.0.1:8000/
```

After that, you can visit the website at `http://127.0.0.1:8000/`. Then you can edit the markdown files and see the changes in real time.

### Modify Docs

Modify the markdown files in the `docs` folder. If you want to modify the table of contents, please modify the `mkdocs.yml` file.

You can follow the [MkDocs](https://squidfunk.github.io/mkdocs-material/) documentation to learn more.

### Publish Docs Website

If you want to submit your changes, please push your changes to your own branch and create a pull request.

```
git checkout -b <Your Branch Name>
git add -u
git commit -m "<Your Message>"
git push origin <Your Branch Name>
```

After merging the pull request, the docs website will be automatically published to [https://docs.chinese-quartet.org](https://docs.chinese-quartet.org).
