# Jupyter Notebook for generating analysis-ready BGC-Argo datasets
Authors: Hakase Hayashida and Haruto Fujishima

## Introduction

1. Identify the float of your interest
1. Download the profiles
1. Visualize the raw data
1. QC to filter out bad data
1. Smooth the data
1. Define the vertical resolution and extent for interpolation
1. Interpolate the data
1. Apply variable-specific post-processing and/or derive additional variables
1. Save to netCDF

## Getting started

```
git clone https://gitlab.com/evparg/analysis-ready-bgc-argo-dataset.git
cd analysis-ready-bgc-argo-dataset # Move to the source code directory
```

For developers only, do the following to configure Git environment for Jupyter Notebook (this needs to be done for the first time only)

```
pip install nbdime nbstripout # Install the relevant packages
nbdime config-git --enable # Configure nbdime
nbstripout --install  # Automatically strip output before committing
```


## Extra