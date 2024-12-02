# Projection of Agricultural Employment

This repository contains a Python script that forecasts agricultural employment for different categories in California until the year 2050. The forecasting is performed using three time series forecasting methods:

- **SARIMAX (Seasonal Autoregressive Integrated Moving Average with Exogenous Regressors)**
- **Prophet**
- **Exponential Smoothing (Holt-Winters Method)**

The results are visualized in a composite figure where each subplot represents a different employment category.

---

## Table of Contents

- [Introduction](#introduction)
- [Methodologies Used](#methodologies-used)
  - [SARIMAX](#1-sarimax)
  - [Prophet](#2-prophet)
  - [Exponential Smoothing](#3-exponential-smoothing)
- [Assumptions and Comments](#assumptions-and-comments)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Code Explanation](#code-explanation)
- [License](#license)

---

## Introduction

Agricultural employment trends are crucial for understanding the economic health and future of the agricultural sector. This project aims to forecast the employment in different agricultural categories in California using historical data and time series forecasting methods. By comparing multiple models, we can better understand potential future trends and make informed decisions.

---

## Methodologies Used

### 1. SARIMAX

- **Description**: A statistical model that captures autocorrelation, trends, and seasonality in time series data.
- **Pros**:
  - Handles complex patterns, including seasonality and trends.
  - Flexible parameters allow for close data fitting.
- **Cons**:
  - Requires careful parameter tuning.
  - Assumes linear relationships.
- **Assumptions**:
  - The time series is stationary or can be made stationary.
  - Residuals are normally distributed and independent.

### 2. Prophet

- **Description**: An additive model developed by Facebook for forecasting time series data with multiple seasonality.
- **Pros**:
  - Automatically detects changes in trends and seasonality.
  - Handles missing data and outliers well.
- **Cons**:
  - May not perform well on data without strong seasonal effects.
  - Can overfit if not properly regularized.
- **Assumptions**:
  - The time series has trend and seasonality components.
  - Observations are independent.

### 3. Exponential Smoothing

- **Description**: Forecasting technique that applies exponentially decreasing weights over time, extended to capture trends and seasonality.
- **Pros**:
  - Simple and efficient for data with stable seasonality.
  - Easy to implement.
- **Cons**:
  - Less effective with complex patterns or changing seasonality.
  - Assumes future patterns will mimic past patterns.
- **Assumptions**:
  - The time series components (level, trend, seasonality) are additive.
  - Patterns are consistent over time.

---

## Assumptions and Comments

- **Data Assumptions**:
  - The time series data is monthly and spans a sufficient time period to capture trends and seasonality.
  - Rhere are none missing values.
- **Model Assumptions**:
  - Each model's assumptions (listed above) hold true for the data.
  - The parameters used are basic and may need tuning for better accuracy.
- **General Comments**:
  - Forecasts are based on historical data patterns and assume these patterns continue into the future.
  - External factors not present in the historical data can affect future employment trends.
  - It's recommended to evaluate the models' performance using appropriate metrics and possibly incorporate additional variables for improved forecasts.

---

## Prerequisites

- Python 3.x
- Libraries:
  - pandas
  - numpy
  - matplotlib
  - seaborn
  - statsmodels
  - prophet (formerly `fbprophet`)
  
---

## Installation

1. **Clone the repository**:

   ```bash
   git clone https://github.com/yourusername/agricultural-employment-forecast.git
   ```

2. **Navigate to the project directory**:

   ```bash
   cd agricultural-employment-forecast
   ```

3. **Install the required libraries**:

   
   ```bash
   pip install pandas numpy matplotlib seaborn statsmodels prophet
   ```

   **Note**: For `prophet`, depending on your environment, you might need to install it using:

   ```bash
   pip install prophet
   ```

---

## Code Explanation

The script performs the following steps:

### 1. Import Necessary Libraries

Imports all required libraries for data manipulation, visualization, and modeling.

### 2. Read and Process the Dataset

- Reads the CSV file into a pandas DataFrame. The data sets were obtained from: [DOWNLOAD!!](https://labormarketinfo.edd.ca.gov/data/ca-agriculture.html)
- Transposes the DataFrame to have dates as rows and categories as columns.
- Converts the index to datetime objects.
- Cleans the data by removing commas and converting strings to numeric values.
- Ensures the data is sorted by date and has a monthly frequency.

### 3. Plot the Historical Time Series Data

Visualizes the historical employment data for each category to understand the trends and patterns.

### 4. Forecasting and Plotting

- **Loop Over Each Category**:
  - Prepares the data for each forecasting model.
  - Creates future dates up to December 2050.
  
- **SARIMAX Model**:
  - Specifies order and seasonal parameters.
  - Fits the model and forecasts future values with confidence intervals.

- **Exponential Smoothing Model**:
  - Fits the Holt-Winters model with additive trend and seasonality.
  - Forecasts future values.
  - Manually calculates confidence intervals using the residuals.

- **Prophet Model**:
  - Prepares the data in the required format with 'ds' and 'y' columns.
  - Fits the model and predicts future values with confidence intervals.

- **Plotting**:
  - Creates a composite figure with subplots for each category.
  - Plots the historical data and forecasts from all three models.
  - Adds confidence intervals and customizes the plot aesthetics.


## License

This project is licensed under the MIT License 
---

*Feel free to contribute to this project by opening issues or submitting pull requests.*
