---
title: "Time Series Analysis"
topic: true
subjects: ['R']
subjects_weight: 120
draft: true
---

- Introduction
	* What is a Time Series?
	* Examples
	* Stationarity
- Time Series Objects
	* Base Representation
		- Creating a `ts` object
		- Visualisation
		- Data quality, outliers and missing data
	* Other Representations
		- `xts`
- Exploratory Analysis
- Correlation
	* Cross-Correlation
		- Correlation and causality
		- Significance
	* Autocorrelation
	* Partial Autocorrelation
- Model Principles
	* Accuracy and Precision
	* Training and Testing
	* Accuracy metrics
	* Rare Events and Black Swans
- Decomposition
	* Moving averages and smoothing
	* Additive and Multiplicative Decomposition
	* Trend
	* Seasonality
	* STL Decomposition
	* Decomposition and Forecasting
- ARIMA
	* Stationarity Revisited
	* Autoregressive (AR) models
	* Moving Average (MA) models
	* Integration
	* Correlations and ARIMA Models
	* Simulating ARIMA
	* Fitting ARIMA
	* Forecasting with ARIMA Models
- Exponential Smoothing
	* Simple Exponential Smoothing
	* The Holt Method
	* The Holt-Winters Method
	* Fitting Exponential Smoothing
	* Forecasting with Exponential Smoothing Models
- Exogenous Variables
	* Examples
	* Adding Exogenous Variables to a model
	* ARMAX and ARIMAX models
	* Predicting with Exogenous Variables
- Prophet