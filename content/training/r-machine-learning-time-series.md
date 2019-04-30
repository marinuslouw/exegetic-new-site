---
title: "Machine Learning: Time Series"
topic: true
subjects: ['R']
subjects_weight: 43
draft: false
---

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