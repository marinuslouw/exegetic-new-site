---
title: "Machine Learning: Linear Models"
topic: true
subjects: ['R']
subjects_weight: 42
draft: false
---

<!--
	http://www.quantide.com/winter-courses-opening-r-data-science-statistics-data-science/
-->

Learn to build a variety of Linear Models using R.

## Contents

- Motivating Example
- k-Nearest Neighbours
- Background
	- Residuals
	- Best fit and least squares
- Linear Regression
	* Assumptions 
	* Multiple regression
	* Model evaluation (RMSE, [MAE](https://en.wikipedia.org/wiki/Mean_absolute_error) and [MPE](https://en.wikipedia.org/wiki/Mean_percentage_error))
	* Categorical and dummy variables
	* Formulae
		* Simple Formulae
		* Interactions
	* Example: Prostate Cancer Data
	* Example: Prostate Cancer Data with Interactions
	* Polynomial regression
	* LOESS
- Validating Model Assumptions
	* Fit Diagnostics
- Using [`{broom}`](https://github.com/tidyverse/broom)
- Generalised Linear Models
	- Logistic regression
		- Thresholding and classification
		- Beyond binary: One-versus-rest models
		- Model evaluation
	- Poisson regression
- Feature Importance
- Feature Selection
  	* Stepwise (forward selection and backward elimination)
- Regularisation
	* Lasso and Ridge Regression
- Generalized Additive Models
- Mixed Effects Models
- Using [`{caret}`](http://topepo.github.io/caret/index.html)
	* pre-processing;
	* train/test splitting;
	* feature importance and feature selection;
	* model evaluation (using cross validation and bootstrapping);
	* model tuning.