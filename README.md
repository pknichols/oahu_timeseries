# Metabarcoding sequence data and analyses for O'ahu timeseries study

Nichols PK & Marko PB (_in prep._). *Spatial complexity, not temporal noise, structures eDNA community profiles on coral reefs.*

This repository contains VSEARCH command line codes and R scripts for the analysis of environmental DNA (eDNA) metabarcoding sequence data.

The dataset includes the following files:

## 1. VSEARCH commands

1. **[VSEARCH.txt](./VSEARCH.txt)**
   *VSEARCH command lines for processing of DNA sequences*
   
## 2. Workflow Steps

1. **[1_Preprocessing18S.Rmd](./1_Preprocessing18S.Rmd)**
   *INSECT taxonomy classification and decontamination of 18S data.*

2. **[2_18S.Rmd](./2_18S.Rmd)**
   *Taxon filtering, read normalization, community and statistical analyses for 18S dataset.*

3. **[3_PreprocessingCOI.Rmd](./3_PreprocessingCOI.Rmd)**
   *INSECT taxonomy classification and decontamination of COI data.*

4. **[4_COI.Rmd](./4_COI.Rmd)**
   *Taxon filtering, read normalization, community and statistical analyses for COI dataset.*

5. **[5_CombinedAnalyses.Rmd](./5_CombinedAnalyses.Rmd)**
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
