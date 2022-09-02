[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.6299024.svg)](https://doi.org/10.5281/zenodo.6299024)

# landslide-seasonality
*Bayesian models to learn seasonal patterns of landslide activity from inventory data*

This repository contains notebooks that perform the analysis reported by: 

**Luna, L.V., Korup, O. Seasonal landslide activity lags annual precipitation pattern in the Pacific Northwest.  Submitted to *Geophysical Research Letters*.**

### 01_LandslideInventoryProcessing.ipynb
This Python Jupyter Notebook reads in the raw landslide inventory data from each source, subsets it to landslides with a known month, and summarizes the counts of landslides that occurred in each month in each inventory.  It creates Figure 1 and Table S1.  It also clips the PRISM 30-year climate normals and  monthly precipitation data to each inventory footprint and summarizes the data.

It produces `footprint_precip.csv`, `slidesallmi.csv`, and `slidesallmi_mrain.csv` which are read into the following R notebooks for model fitting and plotting.

`slidesallmi.csv` contains the counts of landslides that occurred in each month recorded in each landslide inventory.
`slidesallmi_mrain.csv` contains the counts of landslides that occurred in each month along with the monthly average rainfall over the footprint areas.
`footprint_precip.csv` contains the mean annual precipitation for the footprint area of each inventory, calculated from the [PRISM Climate Normals 1991-2020 dataset](https://prism.oregonstate.edu/normals/) (PRISM Climate Group, 2021).

### 02_Models.Rmd
This R Markdown notebook fits the landslide-only single-inventory and multi-inventory negative binomial and logistic regression models and the landslide-precipitation models.  It also explains the model set up in detail.

### 03_Plots.Rmd
This R Markdown notebook produces posterior predictive distributions from each of the fitted models and creates Figures 2, 3, S1-4.  
