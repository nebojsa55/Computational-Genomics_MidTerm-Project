<a href = 'https://github.com/scikit-learn/scikit-learn'><img src="https://img.shields.io/badge/scikit--learn-0.24.1-blueviolet" style="float: left; margin-right: 10px;" /></a>

# Preterm Birth Prediction Challenge

This project was completed as part of the [Computational Genomics](https://www.etf.bg.ac.rs/en/fis/karton_predmeta/13M111GI-2013#gsc.tab=0) course at the University of Belgrade, [School of Electrical Engineering](https://www.etf.bg.ac.rs/en).

The goal was to predict [gestational age](https://en.wikipedia.org/wiki/Gestational_age) in pregnant women by analyzing gene expression via **Regression Models**.

## Data

<a href = 'https://www.synapse.org/#!Synapse:syn18380862/wiki/590485'><img src="docs/Preterm Birth Prediction Banner.png" style="float: left; margin-right: 10px;" /></a>

> The Datasets used for the analyses described in this project were contributed by Wayne State University School of Medicine Perinatal Initiative and by the Perinatology Research Branch, Division of Obstetrics and Maternal-Fetal Medicine, Division of Intramural Research, Eunice Kennedy Shriver National Institute of Child Health and Human Development, National Institutes of Health, U.S. Department of Health and Human Services (NICHD/NIH/DHHS); and, in part, with Federal funds from NICHD/NIH/DHHS under Contract No. HHSN275201300006C. They were obtained as part of the DREAM Preterm Birth Prediction Challenge through Synapse (syn18380862), managed by Sage Bionetworks.

*To learn more please click on the picture above.*

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

## Table of contents and results

The project is divided into **3** [Jupyter notebooks](https://github.com/nebojsa55/Computational-Genomics_MidTerm-Project/tree/master/notebooks), which simulate the thought flow that went to building the model. The main metric regression score was **RMSE (root mean square error)**.
1. [Basic-regression-models.ipybn](https://github.com/nebojsa55/Computational-Genomics_MidTerm-Project/blob/master/notebooks/1.%20Basic-regression-models.ipynb)
   - Samples were standard scaled according to the belonging batch
   - **PCA** analysis was performed to acquire a minimum number of components to account for 95% variance
   - **Random Forest Regressor** and **Support Vector regressor** were tested as they are one of the most common ML models used in literature
   - Hyperparameter cross-validation and 10-fold cross-validation were performed in order to get the best model possible
   - RMSE(RFR) = **7.5441**  ;  RMSE(SVR) = **8.4081** 
   
   
2. [Better-model.ipybn](https://github.com/nebojsa55/Computational-Genomics_MidTerm-Project/blob/master/notebooks/2.%20Better-model.ipynb)
   - Samples were standard scaled according to the belonging batch
   - Instead of PCA, features were selected according to the [*f_regression*](https://scikit-learn.org/stable/modules/generated/sklearn.feature_selection.f_regression.html) score and [*SelectKBest*](https://scikit-learn.org/stable/modules/generated/sklearn.feature_selection.SelectKBest.html) class from *sklearn.feature_selection* module
   - Samples from the set **'GSE113966'** were dropped as they seem to be outliers (32 in total)
   - Random Forest Regressor and Support Vector regressor were tested with the parameters found in notebook 1 through different parameter **K** to find the optimal number of features to use. After that, 10-fold cross-validation was performed
   - RMSE(RFR) = **5.9324**  ;  RMSE(SVR) = **8.0756** 
3. [Linear-regression.ipybn](https://github.com/nebojsa55/Computational-Genomics_MidTerm-Project/blob/master/notebooks/3.%20Linear-regression.ipynb)
   - Samples were standard scaled according to the belonging batch
   - Only linear regressor [**ElasticNet**](https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.ElasticNet.html) was considered, as results from the previous notebook suggest that linear regressors are most suitable for this dataset (*f_regression* score is linear regression test) 
   - 10-fold cross-validation was performed to find optimal parameters for *ElasticNet* regressor and cross-validation was performed for the parameter K in *SelectKBest*
   - RMSE(EN) = **4.9283**
