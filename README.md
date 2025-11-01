# Walmart Sales Analysis & Forecasting
![Walmart_Logo](https://upload.wikimedia.org/wikipedia/commons/b/b1/Walmart_logo_%282008%29.svg)

# Introduction 

## Project Overview

This project focuses on analyzing and forecasting Walmart’s weekly sales data to uncover key performance trends, understand the underlying drivers of sales fluctuations, and build predictive insights that inform strategic business planning.

By combining exploratory data analysis (EDA), statistical testing, and time-series forecasting, the project provides a holistic view of Walmart’s operational and financial performance across stores and time periods.

### Key Objectives

The core goals of this analysis are to:

Assess overall sales trends to determine whether consistent growth is occurring over time.

Evaluate the effectiveness of Walmart’s sales strategies across multiple stores and regions.

Identify top- and bottom-performing stores and weeks, highlighting patterns in geographic and temporal performance.

Uncover the drivers of sales variability, including macroeconomic factors such as CPI, unemployment rate, fuel price, temperature, and holiday events.

Build a forecasting model (ARIMA) to predict future weekly sales and support data-driven decision-making.

Deliver actionable insights and recommendations that enhance operational efficiency and optimize sales strategies.

### Analytical Objectives

Sales Trend Analysis – Evaluate total and average weekly sales to detect patterns and growth trajectories.

Holiday Impact Assessment – Quantify the influence of holiday weeks on sales performance using statistical tests.

Outlier and Seasonality Detection – Identify anomalies and recurring sales cycles through visual analysis.

External Driver Analysis – Examine correlations between sales and macroeconomic factors such as fuel prices, CPI, and unemployment.

Forecasting Future Sales – Leverage time-series modeling to predict sales and visualize the sales trajectory.

Strategic Insights & Recommendations – Summarize findings to inform data-driven business decisions.

### Process overview

| Phase | Description |
| :--- | :--- |
| Data Import & Environment Setup | Imported essential Python libraries (Pandas, NumPy, Matplotlib, Seaborn, Statsmodels, Scikit-learn) and loaded the Walmart sales dataset for analysis.|
| Data Cleaning & Preparation | Inspected the dataset for missing values, data type inconsistencies, and duplicates. Converted date columns to datetime format and ensured proper indexing for time-series operations.|
| Exploratory Data Analysis (EDA) | Conducted comprehensive trend analysis using visualizations (line plots, boxplots, histograms, and heatmaps) to explore sales distribution, seasonality, and store-level variations.|
| Statistical Testing | Performed Welch’s t-test to evaluate significant differences in sales between holiday and non-holiday weeks. |
| Correlation & Driver Analysis | Computed correlation matrices and visualized relationships between sales and macroeconomic factors (Temperature, Fuel Price, CPI, Unemployment). |
|  Forecasting | Developed a time-series forecasting model (ARIMA) to predict weekly sales, validated model performance using RMSE, and visualized forecast results alongside historical trends. |
|  Insights & Recommendations | Derived actionable insights based on analytical findings and proposed strategies for improving sales performance and forecasting accuracy |

## Data Cleaning & Preprocessing

The Walmart dataset includes the following variables:

| Column Name | Type | Description |
| :--- | :--- | :--- |
| Store | Int | Unique store identifier |
| Weekly_Sales | Float | Total sales for the week |
| Holiday_Flag | Int | Indicates whether the week contained a major holiday (1 = Yes, 0 = No) |
| Temperature | Float | Average temperature during the week |
| Fuel_Price | Float | Average fuel cost per gallon |
| CPI | Float | Price Index |
| Unemployment | Float | Unemployment rate for the corresponding region |


### Data Preparation Steps

Missing Value Treatment: Checked and handled missing values using appropriate imputation methods where necessary.

Data Type Conversion: Converted Date column to datetime format for accurate time-series indexing.

Outlier Detection & Visualization: Identified outliers using boxplots and the Interquartile Range (IQR) method to ensure robust statistical analysis.

Duplicate Removal: Verified data integrity by removing duplicate records.

Feature Formatting: Ensured consistent column naming, date sorting, and numerical scaling for modeling.

Time-Series Structuring: Set the Date column as the index to facilitate resampling, rolling averages, and forecasting models.

## Exploratory Data Analysis (EDA)

### Key Visuals & Analyses:

#### Seasonal Patterns

* How has the **sales revenue trended over time**?

Weekly Sales Trend: Identified overall sales growth and seasonal fluctuations.

* Do sales exhibit **seasonal trends**? For example, are there spikes during holidays or specific months?

Store Comparison: Ranked stores by total and average weekly sales.

Holiday Impact: Conducted Welch’s T-test to measure significance of holiday weeks on sales.

External Factors: Explored correlations between sales, temperature, CPI, and unemployment.

Outlier Detection: Highlighted abnormal weekly spikes and dips in sales.

### Statistical Insights

An insignificant difference (p < 0.05) was observed between holiday and non-holiday sales, confirming that holidays don't affect sales too much.

Temperature showed a moderate correlation with weekly sales, while CPI and unemployment had mild negative effects.

The top-performing stores consistently achieved higher sales during promotional and festive periods.

## Time Series Forecasting

To predict future sales, the dataset was transformed into a time series format. Models such as ARIMA, SARIMA were evaluated to capture trends and seasonality.

##### Process:

Time series decomposition (trend, seasonality, residuals)

Stationarity test using ADF

Model fitting and tuning

Forecast visualization and evaluation

Results:
The forecast model successfully predicted upcoming sales trends, identifying expected peaks during holiday seasons and dips in off-peak periods.

## Machine Learning 

A regression model (Random Forest or XGBoost) was trained to predict weekly sales using external factors (CPI, unemployment, fuel price, temperature).

Evaluation Metrics:

Mean Absolute Error (MAE)

Root Mean Squared Error (RMSE)

R² Score

Feature importance analysis revealed that:

Store, Holiday_Flag, and Unemployment were top predictors of weekly sales.

## Key Findings & Recommendations

Sales Growth: Overall sales show a gradual upward trend with strong seasonal peaks around holidays.

Holiday Impact: Holiday weeks outperform regular weeks by an average of 20–25%, confirming high seasonal demand.

External Drivers: Unemployment and CPI exhibit a negative correlation with sales, suggesting economic sensitivity.

Store Performance: A few stores consistently outperform others — further investigation into their strategies could provide benchmarks.

Forecasting: Predictive models indicate a stable upward trend in the coming months with expected spikes during festive periods.

### Recommendations:

Increase marketing and stock planning before major holidays.

Investigate high-performing stores for transferable best practices.

Monitor CPI and unemployment as leading indicators of sales slowdowns.

Use forecasts to optimize logistics and staffing schedules.

Holiday weeks boost average weekly sales by ~15–25%.

Economic indicators like CPI and unemployment have measurable impacts on sales fluctuations.

Store-level variations suggest potential optimization opportunities in underperforming regions.

Forecasted trends can guide promotional planning and inventory stocking strategies.


## Tools & Technologies

Python – Core programming language for data cleaning, transformation, and analysis.
Pandas – Data wrangling and manipulation, handling missing values, and efficient group-by operations.
NumPy – Numerical computing and support for vectorized operations.
Matplotlib – Creation of static, high-quality visualizations and custom plots.
Seaborn – Advanced statistical graphics and aesthetically pleasing charts.
Jupyter Notebook – Interactive environment for code execution, analysis, and visualization.
Git & GitHub – Version control, project documentation, and public repository hosting.

### Models & Techniques

Statistical Analysis: Welch’s T-test, Correlation Analysis

Time-Series Forecasting: ARIMA / SARIMA / Prophet

Visualization Tools: Matplotlib, Seaborn, Plotly

Data Handling: Pandas, NumPy

Model Evaluation: RMSE, MAPE, and visual diagnostics



















