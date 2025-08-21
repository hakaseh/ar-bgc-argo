# Jupyter Notebook for generating analysis-ready BGC-Argo datasets

[:japan: 日本語はこちら](#解析可能な生物地球化学アルゴデータセットを作成するためのjupyter-notebook)

Developers: Hakase Hayashida (JAMSTEC) and Haruto Fujishima (Tohoku University)

This repository provides Jupyter Notebooks for post-processing the profiles of BGC-Argo floats to make them "analysis-ready" by quality-control (QC) filtering, smoothing, and interpolation. Variable-specific treatment (e.g., NPQ correction for chlorophyll-a) and additional variables (e.g., mixed-layer depth) are derived and saved as a netCDF file together with other BGC variables.

If you use our notebook, please cite the corresponding paper (TBD).

## Contents
This repository contains Jupyter Notebooks that do the following:

- Search for BGC-Argo float(s) of your interest (`search.ipynb`)
- Download the profiles of a selected float (`download.ipynb`)
- Generate the analysis-ready dataset of a selected float (`generate.ipynb`)

### `search.ipynb`
***You can skip this notebook if you already have specific float(s) in mind***

This notebook searches for BGC-Argo floats based on the user's selection criteria such as spatial coverage, time period, and variables.

This notebook is recommended for users who are looking for floats that have:
- a consistent sampling frequency () 
- at least for a specific duration ()
- the drifting speed of the float is relevant ()

If none of the above are relevant, we recommend other tools such as [Argo Fleet Monitoring](https://fleetmonitoring.euro-argo.eu/dashboard?Status=Active), which may be easier to use for searching.

### `download.ipynb`
***You can skip this notebook if you have already downloaded the profiles of the float of your interest.***

This notebook downloads the profiles of a selected float using `wget`.

### `generate.ipynb`
This is the main notebook, which post-processes the raw data by filtering, smoothing, and interpolation to make them "analysis-ready". Specifically, it will take the following steps and produces figures (*.png) and a netCDF file at the end:

1. Visualize the raw data. `fig-raw-*.png`
1. Filter out bad data based on QC flags (default: 1, 2, 5, 8). `fig-good-*.png`
1. Smooth the data using *n*-point median filter where *n* is determined based on the vertical resolution, following [Schmechtig et al. 2023](https://archimer.ifremer.fr/doc/00243/35385/). `fig-smooth-*.png`
1. Interpolate the data at defined depths. `fig-int-*.png`
1. Apply additional treatments and derivations. `fig-extra-*.png`
1. Save as a netCDF file. `AR[WMOID].nc` where `AR` stands for Analysis-Ready and `[WMOID]` is the WMO ID of the selected float.

Users need to provide the WMO ID of the float and the vertical resolution and extent used for interpolation.

## Getting started

### Download source code using git (or not using git)
If you are familiar with git, do the following to download source code:
```
git clone https://gitlab.com/evparg/analysis-ready-bgc-argo-dataset.git
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

## Notes

### Techincal details on the data
- We post-process **adjusted** values of the **synthetic** profiles in both **real-time** and **delayed** mode.

### Developers
For developers, do the following to configure git environment for Jupyter Notebook (this needs to be done for the first time only). This will strip output in the notebooks before committing, which makes code changes trackable.
```
pip install nbdime nbstripout
nbdime config-git --enable
nbstripout --install  # Automatically strip output before committing
```

---

# 解析可能な生物地球化学アルゴデータセットを作成するためのJupyter Notebook

開発者：　林田博士（海洋研究開発機構）・藤島遼人（東北大学）

このレポジトリでは、生物地球化学アルゴ(BGC-Argo)フロートのプロファイルをフィルタリング・スムージング・内挿といった後処理を施して"解析可能"なデータセットを作成するJupyter Notebookを提供しています。

ノートブックを使われる際は、こちらの文献の引用をお願いいたします。

## 構成
このレポジトリは以下のJupyter Notebookで構成されています：

- ユーザーのニーズに合ったフロートを検索するノートブック (`search.ipynb`)
- 選択したフロートのプロファイルをダウンロードするノートブック (`download.ipynb`)
- 選択したフロートのプロファイルを解析可能なデータセットにするノートブック (`generate.ipynb`)

### search.ipynb
***後処理したいフロートがすでに決まっている場合はこのノートブックは実行する必要はありません***

