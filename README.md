## Hackathon Smartness / 5G Dataset Challenge

# Overview

The advancement of 5G is one of the most significant transformations in the technology world in recent years, and Brazil is not lagging behind in this race. With unprecedented latency and data transmission speed, 5G promises to revolutionize human connectivity and communication, as well as enable endless new opportunities for innovation and entrepreneurship in various areas such as healthcare, agriculture, industry, and much more.

In this context, the _Hackathon SMARTNESS / 5G Dataset Challenge_ aims to stimulate the development of innovative solutions and the elaboration of _insights_ using databases (provided by the organizing committee of Hackathon SMARTNESS) composed of data on the use of adaptive video streaming services (YouTube) and 5G networks in Brazil. To support the problem solving, teams will be able to use auxiliary databases for data enrichment.

Teams will be able to develop their projects in several lines, such as, for example, exploratory data analysis, development of innovative _insights_ using 5G and the datasets made available, Machine Learning models for prediction, classification, clustering, decision support, development of application performance models in the context of 5G and much more.

# Requirements

To develop solutions for the Hackathon, it is necessary to have a computer to perform data processing and Machine Learning in _Jupyter Notebook_.

In addition, it is desirable that participants have knowledge in the following subjects:

* Data processing and analysis;
* Machine Learning methods, such as regression, clustering, decision trees, random forests (_Random Forest_), k-nearest neighbors (kNN), linear discriminant analysis;
* Programming in _Python_; and
* _Jupyter Notebook_.

# 1st Step: Preparing the Execution Environment

## Google Colab

It is possible to use this repository online, without additional configurations. Just click on the Google Colab _badge_ in the Notebooks you want to run.

Make a copy of the Notebook to edit the content.

Be sure to execute the cell that indicates `Google Colab environment configuration` before any other so that the environment is configured properly.

## Locally

This repository can be run locally using the Mamba: [https://mamba.readthedocs.io/en/latest/installation.html](https://mamba.readthedocs.io/en/latest/installation.html) or Conda: [https://docs.conda.io/projects/conda/en/latest/user-guide/install/index.html](https://docs.conda.io/projects/conda/en/latest/user-guide/install/index.html) environment, and downloading the additional datasets.

1. Clone the repository on your machine inside the desired folder:

```
git clone --depth=1 https://github.com/intrig-unicamp/hackathon5G.git
cd hackathon5G
```

2. Create the environment from the `environment.yml` file:

```
# if using Micromamba:
micromamba env create -f environment.yml -y

# if using Conda:
conda env create -f environment.yml
```

3. Activate the environment:

```
# if using Micromamba:
micromamba activate hackathon5G

# if using Conda:
conda activate hackathon5G
```

4. Start Jupyter Lab. If a browser window does not open with Jupyter Lab, just click on one of the access links available in the terminal:

```
jupyter lab
```

# 2nd Step: Datasets

See here: datasets the folder with the databases made available and their respective documentation in the README: datasets/README.md of this folder.

# 3rd Step: Challenges

See here: challenges the folder with the proposed challenges. The README: challenges/README.md of this folder provides the necessary instructions on each challenge. Auxiliary Notebooks are also provided for teams to start developing the challenges more quickly.

# 4th Step: Submission

**Google Forms: [https://forms.gle/9Gnv8NFdCVPkLFQ99](https://forms.gle/9Gnv8NFdCVPkLFQ99) for submitting solutions**

Teams should submit the Jupyter Notebook files produced in each solution, which should contain a data storytelling covering the description of what was done by the team, the insights obtained, the pre-processing, the Machine Learning models developed, the performance evaluation of the models, the choice of the Machine Learning model, among other topics that the teams deem pertinent.

Pay attention to the challenges roadmap, the evaluation criteria and the differentiated delivery of some challenges. Ensure that the evaluators of the Hackathon SMARTNESS organizing committee have access to all files in your submission. Teams must ensure that they provide all other datasets they used. Preferably, download the necessary data as follows:

```python
# ✅ Recommended
# > clone a GitHub repository. Example:
!git clone --depth=1 https://github.com/intrig-unicamp/hackathon5G.git

# ✅ Recommended
# > download a file