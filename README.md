# Jupyter Notebook for generating analysis-ready BGC-Argo datasets
Authors: Hakase Hayashida (JAMSTEC) and Haruto Fujishima (Tohoku University)

This repository provides Jupyter Notebooks for post-processing the profiles of a selected BGC-Argo float to make them "analysis-ready" by filtering the raw data via quality-control (QC) flags and smoothing and then interpolating each profile to common depths. Variable-specific treatment (e.g., NPQ correction for chlorophyll-a) and additional variables (e.g., mixed-layer depth) are derived and saved as a netCDF file together with other BGC variables.

## Contents
This repository contains Jupyter Notebooks that do the following:

1. Search for BGC-Argo float(s) of your interest (`search.ipynb`)
1. Download the profiles of a selected float (`download.ipynb`)
1. Generate the analysis-ready dataset of a selected float (`generate.ipynb`)

### search.ipynb
***You can skip this notebook if you already have specific float(s) in mind***

This notebook searches for BGC-Argo floats based on the user's selection criteria such as spatial coverage, time period, and variables.

This notebook is recommended for users who are looking for floats that have:
- a consistent sampling frequency () 
- at least for a specific duration ()
- the drifting speed of the float is relevant ()

If none of the above are relevant, we recommend other tools such as [Argo Fleet Monitoring](https://fleetmonitoring.euro-argo.eu/dashboard?Status=Active), which may be easier to use for searching.

### download.ipynb
***You can skip this notebook if you have already downloaded the profiles of the float of your interest.***

This notebook downloads the profiles of a selected float using `wget`.

### generate.ipynb
This notebook is the core of the project and it post-processes the raw data by filtering, smoothing, and interpolation to make them "analysis-ready".

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