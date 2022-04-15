---
hide:
  - navigation
  # - toc
---

## NOTES
- These fields are applicable to all omics technologies.
- If there is something you do not understand, please download the historical metadata at the Quartet Data Portal to learn more about its meaning.
- The "from" column indicates the source of the field.

## Metadata Schema
|key | name | short | description | type | collection | from|
|----|------|-------|-------------|------|-----------|----|
|project_id | Project Id | Project Id | Identity of the project. | category | quartet | project|
|project_name | Project Name | Project Name | Name of the project. | category | quartet | project|
|project_type | Project Type | Project Type | Type of the project. | category | quartet | project|
|project_description | Project Description | Project Description | Description of the project. | category | quartet | project|
|investigator_name | Investigator Name | Pi Name | Name of the investigator. | category | quartet | project|
|investigator_affiliation | Investigator Affiliation | Pi Aff | Affiliation of the investigator. | category | quartet | project|
|support_id | Support Id | Support Id | ID of the project funded. | category | quartet | project|
|support_source | Support Source | Support Source | Source of the project funded. | category | quartet | project|
|date_collected | Date Collected | Date Collect | Collection date. | number | quartet | project|
|availability_type | Availability Type | Avail Type | Data privacy. | category | quartet | project|
|donor_id | Donor Id | Donor Id | Identity of the donor. | category | quartet | donor|
|family_id | Family Id | Family Id | Identity of the family. | category | quartet | donor|
|pedigree | Pedigree | Pedigree | Pedigree of the family | category | quartet | donor|
|gender | Gender | Gender | Gender of the donor. | category | quartet | donor|
|birth_date | Birth Date | Birthday | Birthday of the donor. | number | quartet | donor|
|biospecimen_id | Biospecimen Id | Biospecimen Id | Identity of the biospecimen. | category | quartet | biospecimen|
|biospecimen_name | Biospecimen Name | Biospecimen Name | Name of the biospecimen. | category | quartet | biospecimen|
|biospecimen_type | Biospecimen Type | Biospecimen Type | Type of the biospecimen. | category | quartet | biospecimen|
|collection_date | Collection Date | Collect Date | Sample collection date. | number | quartet | biospecimen|
|rm_id | Rm Id | Rm Id | Identity of the RM. | category | quartet | reference_materials|
|extraction_site | Extraction Site | Extract Site | Site of the extraction. | category | quartet | reference_materials|
|lot_no | Lot No | Lot No | Number of batch. | number | quartet | reference_materials|
|cell_line_passage_number | Cell Line Passage Number | Clp Number | Number of cell line passage. | number | quartet | reference_materials|
|rm_type | Rm Type | Rm Type | Type of the RM. | category | quartet | reference_materials|
|source | Source | Source | Source of the sample.(eg. Blood, cell, etc.) | category | quartet | reference_materials|
|cell_collection_date | Cell Collection Date | Cell Collect Date | Data of cell collcollectionction. | number | quartet | reference_materials|
|extraction_date | Extraction Date | Extract Date | Data of materials extraction. | number | quartet | reference_materials|
|kit_cat_no | Kit Cat No | Kit Cat No | Number kit cat. | number | quartet | reference_materials|
|kit_lot_no | Lot Lot No | Kit Cat | Number kit lot. | number | quartet | reference_materials|
|extraction_protocol | Extraction | Extract | Protocol of extraction. | number | quartet | reference_materials|
|library_id | Library Id | Library Id | Identity of the library. | number | quartet | library|
|input_ng | Input Ng | Input Ng | Concentration of input. | precision | quartet | library|
|enrich_kit | Enrich Kit | Enrich Kit | Kit of library enrichment. | category | quartet | library|
|preparation_kit | Preparation Kit | Prep Kit | Kit of preperation. | category | quartet | library|
|fragment_method | Fragment Method | Fragment Method | Method of the fragment. | category | quartet | library|
|fragment_selection | Fragment Selection | Fragment Select | Selection of the fragment. | category | quartet | library|
|fragment_range | Fragment Range | Fragment Range | Range of the fragment. | precision | quartet | library|
|pcr_cycle | Pcr Cycle | Pcr Cycle | Cycle of PCR | number | quartet | library|
|preparation_date | Preparation Date | Prep Date | Date of preperation. | number | quartet | library|
|spike_in | Spike In | Spike In | Spike_in added in the library construction.PreparationpreparationPreparationpreparation | category | quartet | library|
|qc_concentration | Qc Concentration | Qc Conc | Concentration of quality control. | precision | quartet | library|
|qc_size | Qc Size | Qc Size | Size of quality control. | precision | quartet | library|
|preparation_method | Preperation Method | Prep Method | Method of preparation. | category | quartet | library|
|preparation_site | Preparation Site | Prep Site | Site of preparation | category | quartet | library|
|batch | Library Batch | Lib Batch | Batch of library | category | quartet | library|
|stranded | Library Type | Lib Type | Type of library | category | quartet | library|
|sequencing_id | Sequencing Id | Seq Id | ID of sequencing. | number | quartet | sequencing|
|site | Site | Site | Site of sequencing. | category | quartet | sequencing|
|platform | Platform | Platform | Platform of sequencing. | category | quartet | sequencing|
|method | Method | Method | Method of sequencing. | category | quartet | sequencing|
|index_sequence | Index Sequence | Index Seq | Index of sequencing. | category | quartet | sequencing|
|flowcell_id | Flowcell Id | Flowcell Id | Identity of the flowcell. | category | quartet | sequencing|
|lane_no | Lane No | Lane No | Number of the lane. | number | quartet | sequencing|
|run_date | Run Date | Run Date | Date of process running. | number | quartet | sequencing|
|datafile_id | Datafile Id | Datafile Id | Identity of the data file. | category | quartet | datafile|
|submitter_id | Submitter Id | Submitter Id | Identity of the submitter. | category | quartet | datafile|
|data_type | Data Type | Data Type | Type of the data file. | category | quartet | datafile|
|data_category | Data Category | Data Cat | Category of the data file. | category | quartet | datafile|
|data_format | Data Format | Data Format | Format of the data file. | category | quartet | datafile|
|file_name | File Name | File Name | Name of the data file. | category | quartet | datafile|
|file_size | File Size | File Size | Size of the datafile. | precision | quartet | datafile|
|md_5sum | Md5Sum | Md5 | The 128-bit hash value expressed as a 32 digit hexadecimal number (in lower case) used as a file's digital fingerprint. | category | quartet | datafile|
|file_path | File Path | File Path | Path of the date file. | category | quartet | datafile|
|node | Node Id | Node Id | Identity of the Node URL. | category | quartet | datafile|
|analyses_id | Analyses Id | Analyze Id | Identity of the analyses. | category | quartet | analyses|
|analyses_type | Analyses Type | Analyze Type | Type of the analyses. | category | quartet | analyses|
|link | Link | Link | Link of the analyses. | category | quartet | analyses|
|version | Version | Version | Version of the analyses. | category | quartet | analyses|