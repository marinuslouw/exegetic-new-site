---
title: "Machine Learning: Time Series"
topic: true
subjects: ['R']
subjects_weight: 43
draft: true
---

A Time Series model allows you to make predictions about the future based on observations from the past. These models have important applications in science, industry and commerce.

> *Prediction is very difficult, especially if it's about the future.*<br>&mdash; Niels Bohr, Nobel Laureate (Physics)

Niels Bohr was right: predicting the future is a tough problem. Some things, like lottery numbers, are inherently undepredictable. Others, like air temperatures and rainfall, are reasonably predictable. Time series analysis makes it possible to assess whether or not predictions are possible and, if they are, build a model which can generate informed predictions for the future with realistic estimates of uncertainty.

> *The best qualification of a prophet is to have a good memory.*<br>&mdash; George Savile

This course will provide you with an understanding of the theory behind time series models and the ability to build such models in R. By the end of the course you'll be able to select the appropriate model for your data, train a model and start making predictions.

## Course Content

- Introduction
	* What is a Time Series?
	* Examples
	* Stationarity
- Time Series Objects
	* Base Representation
		- Creating a `ts` object
		- Visualisation: plots and seasonal plots
		- Data quality, outliers and missing data
	* Other Representations
		- `xts`
- Decomposition
	* Moving averages and smoothing
	* Additive and Multiplicative Decomposition
	* Trend
	* Seasonality
	* STL Decomposition
	* Decomposition and Forecasting
- White Noise and Random Walk
	- Stationarity
	- Differencing
- Correlation
	- Covariance and correlation
	- Cross-Correlation
		* Correlation and causality
		* Significance
	- Autocorrelation (ACF)
	- Partial autocorrelation (PACF)
- Model Principles
	* Accuracy and Precision
	* Training and Testing
	* Accuracy metrics
	* Rare Events and Black Swans
- Exponential Smoothing
	- Simulation
	- Model estimation and forecasting
	- Adding trend and seasonality: Holt and Holt-Winters methods
- Moving Average (MA) Models
	- Simulation
	- ACF and moving average
	- Model estimation and forecasting
- Autoregressive (AR) Models
	- Simulation
	- PACF and autoregression
	- Model estimation and forecasting
- ARIMA Models
	- Simulation
	- Integrating for non-stationarity
	- Model estimation and forecasting
	- Automating with `auto.arima()`
- Exogenous Variables
	* Examples
	* Adding Exogenous Variables to a model
	* ARMAX and ARIMAX models
	* Predicting with Exogenous Variables
- Prophet
	- Non-linear and changing trends
	- Multiple seasonalities
	- Non-uniform sampling and missing data

## Course Duration

This course can be presented at either an Introductory or Advanced level.

**Introductory Version** (duration: 1 day) is application oriented and shows how R can be used to solve Time Series problems without digging too deeply into the theoretical details.

**Advanced Version** (duration: 2 days) delves into the theoretical details and explores the theory behind the models.

Both versions cover a similar set of examples and exercises.
