---
layout: post
title:  "Miniconda Setup"
date:   2022-09-15 06:00:00 -0100
week: "1"
number: "1"
categories: "labs"
---

## Materials
* laptop (MacOS or Windows)
* internet access
* Miniconda

### Installation
1. Go [here](https://docs.conda.io/en/latest/miniconda.html#latest-miniconda-installer-links) to download the `Miniconda 3 Installer` for your operating system
2. Once the download has finished run the installer:
    * MacOS: In the Terminal `bash Downloads/Miniconda3-latest-MacOSX-x86_64.sh`
    * Windows: Navigate to Downloads (or wherever you downloaded this) and double click the `.exe` file
3. Follow the installation prompts
4. Update `Miniconda3`:
    * MacOS: In the Terminal `conda update conda`
    * Windows: In Anaconda Powershell Prompt (miniconda3) execute `conda update conda`
5. Agree to the installation prompts

### Environment Setup
1. Create and name a new Python environment `conda create -n physcpu1 python`
2. Activate the environment `conda activate physcpu1`
3. Install Jupyter Notebook via pip `pip install notebook`
4. Run Jupyter Notebook `jupyter notebook`
5. Quick tour of Jupyter Notebook
6. From home page find and click on the `Quit` button to shutdown the server
