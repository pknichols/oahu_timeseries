# Metabarcoding sequence data and analyses for O'ahu timeseries study

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.18400808.svg)](https://doi.org/10.5281/zenodo.18400807)

*Spatial complexity, not natural temporal variability, structures eDNA community profiles on coral reefs*

This repository contains VSEARCH command line codes and R scripts for the analysis of environmental DNA (eDNA) metabarcoding sequence data.

The dataset includes the following files:

## 1. VSEARCH commands

#### A. **[VSEARCH.txt](./VSEARCH.txt)**
   *VSEARCH command lines for processing of DNA sequences*


Step | Input                                   | Output                                         | Description
-----|----------------------------------------|-----------------------------------------------|-------------------------------------------------------------
1    | data_18S.fasta                          | alldata_derep.fasta                           | Dereplicate full-length 18S sequences, remove sequences <30bp or with <2 copies
2    | alldata_derep.fasta                      | alldata_nochimeras.fasta                      | Detect and remove chimeras using de novo uchime_denovo
3    | alldata_nochimeras.fasta                 | data_sorted.fasta                             | Sort sequences by abundance and remove singletons (minsize 2)
4    | data_sorted.fasta                        | data_rep_set_18S.fasta, data_centroids.fasta | Cluster sequences at 99% identity to generate representative OTUs
5    | data_18S.fasta + data_centroids_18S.fasta | dataOTU_18S.txt                              | Map original sequences to representative OTUs to produce final OTU table
6    | data_COI.fasta                           | alldata_derep.fasta                           | Dereplicate full-length COI sequences, remove sequences <30bp or <2 copies
7    | alldata_derep.fasta                      | alldata_nochimeras.fasta                      | Detect and remove chimeras (de novo)
8    | alldata_nochimeras.fasta                 | data_sorted.fasta                             | Sort sequences by abundance and remove singletons (minsize 2)
9    | data_sorted.fasta                        | data_rep_set_COI.fasta, data_centroids_COI.fasta | Cluster sequences at 99% identity to generate representative OTUs
10   | data_COI.fasta + data_centroids_COI.fasta | dataOTU_COI.txt                              | Map original sequences to representative OTUs to produce final OTU table


## 2. Workflow Steps

#### A. **[1_Preprocessing18S.Rmd](./1_Preprocessing18S.Rmd)**
   *INSECT taxonomy classification and decontamination of 18S data.*

#### B. **[2_18S.Rmd](./2_18S.Rmd)**
   *Taxon filtering, read normalization, community and statistical analyses for 18S dataset.*

#### C. **[3_PreprocessingCOI.Rmd](./3_PreprocessingCOI.Rmd)**
   *INSECT taxonomy classification and decontamination of COI data.*

#### D. **[4_COI.Rmd](./4_COI.Rmd)**
   *Taxon filtering, read normalization, community and statistical analyses for COI dataset.*

#### E. **[5_CombinedAnalyses.Rmd](./5_CombinedAnalyses.Rmd)**
   *Producing figures and combined analyses on outputs from both 18S and COI datasets.*


```
├── data/
│   ├── raw/               # Sequence outputs (.fasta) from VSEARCH, .rds INSECT classifiers for 18S and COI, OTU tables from VSEARCH
│   └── processed/         # OTU tables after LULU curation, INSECT-classified taxonomies, Rarefied OTU tables
├── results/
│   ├── figures/           # Figures for manuscript and analyses
│   ├── tables/            # Table results: zeta diversity, stability/synchrony, GLMER, etc.
│   └── rds/               # Large R objects: iNEXT rarefaction, randomForest objects
├── 1_Preprocessing18S.Rmd
├── 2_18S.Rmd
├── 3_PreprocessingCOI.Rmd
├── 4_COI.Rmd
├── 5_CombinedAnalyses.Rmd
├── VSEARCH.txt
└── README.md
```


| Step | File | Description | 
|------|------|-------------|
| 1 | 1_Preprocessing18S.Rmd | imports 18S otu table and grouped sequence .fasta, curates with lulu, classifies taxonomy with INSECT, decontaminates with microDecon | 
| 2 | 2_18S.Rmd | retains metazoan and macroalgal taxa, performs eDNA index normalization, community and statistical analyses for 18S dataset |
| 3 | 3_PreprocessingCOI.Rmd | imports COI otu table and grouped sequence .fasta, curates with lulu, classifies taxonomy with INSECT, decontaminates with microDecon | 
| 4 | 4_COI.Rmd | retains metazoan and macroalgal taxa, performs eDNA index normalization, community and statistical analyses for COI dataset  | 
| 5 | 5_CombinedAnalyses.Rmd | produces main text figures with combined results from both 18S and COI datasets | 


Raw metabarcoding sequences have been submitted to NCBI SRA (BioProject PRJNA1399417). https://dataview.ncbi.nlm.nih.gov/object/PRJNA1399417?reviewer=u0i7n07faajchu46geulelke46


## Citation
Please cite the associated manuscript when using these data.

## License
This repository is licensed under a Creative Commons Attribution 4.0 International License (CC BY 4.0).  
See the LICENSE file for details.
