<a href = 'https://github.com/scikit-learn/scikit-learn'><img src="https://img.shields.io/badge/scikit--learn-0.24.1-blueviolet" style="float: left; margin-right: 10px;" /></a>

# Preterm Birth Prediction Challenge

This project was completed as part of the [Computational Genomics](https://www.etf.bg.ac.rs/en/fis/karton_predmeta/13M111GI-2013#gsc.tab=0) course at the University of Belgrade, [School of Electrical Engineering](https://www.etf.bg.ac.rs/en).

The goal was to predict gestational age in pregnant women by analyzing gene expression via **Regression Models**.

## Data

<a href = 'https://www.synapse.org/#!Synapse:syn18380862/wiki/590485'><img src="docs/Preterm Birth Prediction Banner.png" style="float: left; margin-right: 10px;" /></a>

The data used was from **DREAM Preterm Birth prediction challenge**. *To learn more please click on the picture above*

Data stats:

| Total num of samples  |    Train samples |  Testing samples |Number of features|
|:----------:|:-------------:|:------:|:--------:|
| 735 |  367 | 368 |32 830|

*DISCLAIMER*:
Gestational age in testing data was not provided, due to the nature of the challenge. Because of that, this model was implemented and tested using only 367 samples from original training set. **The challenge has ended in 2019. and this implementation was not an active part of the challenge**

## Requirements

To install the necessary libraries, type in the terminal:
``` shell
pip install -r requirements.txt 
```

## Table of contents



