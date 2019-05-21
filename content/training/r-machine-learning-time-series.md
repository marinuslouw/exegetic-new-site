---
title: "Machine Learning: Time Series"
topic: true
subjects: ['R']
subjects_weight: 43
draft: true
---

TWO VERSIONS OF COURSE BELOW --- MERGE!!

A Time Series model allows you to make predictions about the future based on observations from the past. These models have important applications in science, industry and commerce.

## Contents

- Introduction
	- Creating time series objects
	- Exploring a time series: plots and seasonal plots
- Trends
	- Types of trend (level, variability and seasonal)
	- Removing trend
- White Noise and Random Walk
	- Stationarity
	- Differencing
- Correlation
	- Covariance and correlation
	- Autocorrelation (ACF)
	- Partial autocorrelation (PACF)
- Exponential Smoothing
	- Simulation
	- Model estimation and forecasting
	- Adding trend and seasonality
- Moving Average (MA) Models
	- Simulation
	- ACF and moving average
	- Model estimation and forecasting
- Autoregression (AR) Models
	- Simulation
	- PACF and autoregression
	- Model estimation and forecasting
- ARIMA Models
	- Integrating for non-stationarity
	- Automating with `auto.arima()`
- Prophet
	- Non-linear and changing trends
	- Multiple seasonalities
	- Non-uniform sampling and missing data

# Time Series Analysis with R

> *Prediction is very difficult, especially if it's about the future.* &mdash; Niels Bohr, Nobel Laureate (Physics)

Niels Bohr was right: predicting the future is a tough problem. Some things, like lottery numbers, are inherently undepredictable. Others, like air temperatures and rainfall, are reasonably predictable. Time series analysis makes it possible to assess whether or not predictions are possible and, if they are, b
uild a model which can generate informed predictions for the future with realistic estimates of uncertainty.

> *The best qualification of a prophet is to have a good memory.* &mdash; George Savile

This course will provide you with an understanding of the theory behind time series models and the ability to build such models in R. By the end of the course you'll be able to select the appropriate model for your data, train a model and start making predictions.

## Course Duration

This course can be presented at either an Introductory or Advanced level.

**Introductory Version** (duration: 1 day) is application oriented and shows how R can be used to solve Time Series problems without digging too deeply into the theoretical details.

**Advanced Version** (duration: 2 days) delves into the theoretical details and explores the theory behind the models.

Both versions cover a similar set of examples and exercises.

## Course Content

Below is the outline of the *Time Series Analysis with R* course.

- [Introduction](time-series-introduction.md)
- [Time Series Representation](time-series-representation.md)
- [Correlation](time-series-correlation.md)
- [Exploratory Analysis](time-series-exploratory-analysis.md)
- [Model Principles](time-series-model-principles.md)
- [ARIMA](time-series-arima.md)
- [Exponential Smoothing](time-series-exponential-smoothing.md)
- [Decomposition](time-series-decomposition.md)
- [Exogenous Variables](time-series-exogenous-variables.md)

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