# Jupyter Notebook for generating analysis-ready BGC-Argo datasets
Authors: Hakase Hayashida and Haruto Fujishima

## Introduction
This repository contains Jupyter Notebooks that do the following:

1. Search for BGC-Argo float(s) of your interest (`search.ipynb`)
1. Download the profiles of a selected float (`download.ipynb`)
1. Generate the analysis-ready dataset of a selected float (`generate.ipynb`)

### search.ipynb
***You can skip this notebook if you already have specific float(s) in mind***

This

### download.ipynb
***You can skip this notebook if you have already downloaded the profiles of the float of your interest.***

This

### generate.ipynb
This notebook is the

1. Visualize the raw data
1. QC to filter out bad data
1. Smooth the data
1. Define the vertical resolution and extent for interpolation
1. Interpolate the data
1. Apply variable-specific post-processing and/or derive additional variables
1. Save to netCDF


## Getting started

### Download source code using git (or not using git)
If you are familiar with git, do the following to download source code:
```
git clone https://gitlab.com/evparg/analysis-ready-bgc-argo-dataset.git
```

For **developers only**, do the following to configure git environment for Jupyter Notebook (this needs to be done for the first time only). This will strip output in the notebooks before committing, which makes code changes trackable.
```
pip install nbdime nbstripout
nbdime config-git --enable
nbstripout --install  # Automatically strip output before committing
```
If you are unfamiliar with git, you can download source code by clicking on **Code** (in blue) above and choose **Download source code** (e.g., as a zip file).

### Open Jupyter environment (Notebook or Lab)
This can be done either via clicking or in command line as:
```
jupyter notebook
```
or
```
jupyter lab
```


## Extra