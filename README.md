# MSB1015_Pluim
Githhub repository for programing project.

# Co-abundance network analysis of stool proteomics in IBD

Author: Erik Pluim (i6284718)
Courses: MSB1015 Scientific Programming / MSB1014 Network Biology, Maastricht University

This repository contains a single R Markdown script that analyses a DIA-NN stool proteomics data set from healthy controls (HC, n = 10), irritable bowel syndrome patients (IBS, n = 12) and inflammatory bowel disease patients (IBD, n = 25). 

## What the script does

1. **Import and QC**: reads the DIA-NN protein matrix, builds the log2 intensity matrix and checks sample and mean correlations.
2. **Normalisation and imputation**: PQN normalisation and QRILC imputation of missing values, with PQN and imputation plots.
3. **PCA**: PCA before and after removing sample i11 (PC1/PC2, PC2/PC3, PC1/PC3).
4. **Classifiers**: SVM and random forest with nested cross-validation (5 x 5), a 50-label permutation test, ROC curves and Youden thresholds.
5. **Differential abundance**: proDA, with volcano plot and top-10 table.
6. **Co-abundance networks**: Spearman networks (pooled and per group), partial-correlation check, Louvain community stability, differential co-abundance and network candidates.
7. **STRING**: protein-protein interaction network and permutation tests for the candidate proteins.

## Repository contents

| File | Description |
|---|---|
| `i6284718Pluim_Script_final.Rmd` | The full analysis script |
| `figure/` | All figures produced by the script, pre-rendered here |

## How to run

1. Download or clone the repository and keep all files in the same folder.
2. Open `i6284718Pluim_Script_final.Rmd` in RStudio (or open the folder as an RStudio project).
3. Click **Knit**, or run `rmarkdown::render("i6284718Pluim_Script_final.Rmd")` from this folder.

No working directory needs to be set: knitting runs from the folder the script is in, and the input file is read by name.

The first chunk installs any missing CRAN and Bioconductor packages and loads them, so the first run takes longer. A full knit takes about 19 minutes. Figures are written to `figure/`, and the knitted HTML report is written next to the script.

## Requirements

- R 4.5.2 and RStudio 2026.01.1 (the versions used).
- An internet connection for installing packages and for the STRING queries.
- Packages (installed automatically): readxl, dplyr, tidyr, ggplot2, ggrepel, pheatmap, protti, dendextend, seriation, igraph, parsnip, workflows, tune, rsample, yardstick, dials, recipes, kernlab, ranger, pROC, httr, jsonlite, and from Bioconductor proDA and imputeLCMD.

The full list and versions used are printed at the end of the knitted report (`sessionInfo()`).

## Reproducibility

The random seed is set in the YAML header (`seed: 013`), and every stochastic step (imputation, cross-validation, permutations, network stability tests) reseeds itself from it, so results are reproducible. `ggrepel`, which is used in some plots, is an exception but only effects some graphics, not the results of the figures.

## Data

The data used is unpublished and cannot be included here.

## Use of generative AI
Claude (Anthropic) was used to refined and optimize the R code. All analysis decisions and results are my own.
