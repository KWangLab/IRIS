# IRIS: Immunotherapy Resistance *cell-cell* Interaction Scanner
**Last Updated: 09/24/2024**
<img src="https://github.com/kwangcb/IRIS/blob/main/4-Figure/figures/biorender/png/IRIS%20figure%201%20Final%20Version%20%5Bnc%20acc%5D.png" alt="grouping">

## Overview

We developed **I**mmunotherapy **R**esistance cell-cell **I**nteraction **S**canner (IRIS), an **```R```** package specifically designed to identify immune checkpoint blockade (ICB) resistance relevant ligand-receptor interactions in the tumor microenvironment (TME), given a patients cohort including tumor bulk expression data and ICB treatment response data. The gene expression data is deconvolved using [**CODEFACS**](https://pubmed.ncbi.nlm.nih.gov/34983745/) such that the input to IRIS in a given patients cohort is comprised of two components: 1. Literature-curated cell-type-specific ligand-receptor interaction activity profiles (denoting either activation: 1 or inactivation: 0) in each tumor sample, which is inferred using [**LIRICS**](https://pubmed.ncbi.nlm.nih.gov/34983745/) from the deconvolved expression – an interaction is considered as activated if the (deconvolved) expression of both its ligand and receptor genes is above their median expression values across the cohort samples, and inactivated otherwise;  2. The corresponding ICB response outcome for each patient. 

IRIS consists of two steps: Step I uses a Fisher’s test to identify differentially activated ligand-receptor interactions in the pre-treatment and non-responder post-treatment samples. These interactions are categorized as either resistant downregulated interactions (RDI) or resistant upregulated interactions (RUI) based on their differential activity state in the post-treatment vs. the pre-treatment state; that is, RDIs are downregulated in post-treatment resistant patients and vice versa for RUIs. Step II employs a hill climbing aggregative feature selection algorithm to choose the optimal set of RDIs or RUIs for classifying responders and non-responders in pre-treatment samples. The final output of IRIS is a selected set of RDIs and RUIs hypothesized to facilitate in ICB resistance, that can be used to predict ICB therapy response in a new ICB cohort.

## Installation
```r
install.packages('devtools')
library(devtools)
devtools::install_github("KWangLab/IRIS")
```
## Tutorials
* To reproduce the Nat. Comms. results from Sahni et al., see: https://github.com/KWangLab/IRIS/blob/main/vignettes/IRIS.Rmd
* To implement IRIS in your own work, see: https://github.com/KWangLab/IRIS/blob/main/vignettes/IRIS.Rmd

## Sample data availability
Sample CODEFACS and LIRICS data can be found at https://zenodo.org/records/13172848.

## System requirements
IRIS was developed on R (v4.4.1) using R packages: dplyr (v1.1.4), magrittr (v2.0.3), parallel (v4.4.1), pROC (v1.18.5), rBayesianOptimization (v1.2.1), tidyr (v1.3.1). All analyses were done on R (v4.4.1).

## Citation
If using IRIS, please cite:

Sahni, S., Wang, B., Wu, D. et al. A machine learning model reveals expansive downregulation of ligand-receptor interactions that enhance lymphocyte infiltration in melanoma with developed resistance to immune checkpoint blockade. Nat Commun 15, 8867 (2024). [https://doi.org/10.1038/s41467-024-52555-4](https://rdcu.be/dXbLv)

[Download Citation](https://citation-needed.springer.com/v2/references/10.1038/s41467-024-52555-4?format=refman&flavour=citation)

## Acknowledgement(s)
### Lead Developer(s)
1. **Sahil Sahni**
2. **Kun Wang** (kwang222@illinois.edu)^
3. **Eytan Ruppin** (eytan.ruppin@nih.gov)^

^*equally-contributing corresponding author(s)*

### Acknowledgement(s)
IRIS figure was created with BioRender.com.

