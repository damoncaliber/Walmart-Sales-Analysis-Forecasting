# Walmart Sales Analysis & Forecasting
![Walmart_Logo](https://upload.wikimedia.org/wikipedia/commons/b/b1/Walmart_logo_%282008%29.svg)

# Introduction 
**Walmart Inc.**, founded in 1962 by Sam Walton and headquartered in Bentonville, Arkansas, is the world’s largest retail corporation, operating over 10,000 stores and serving more than 230 million customers weekly across 20+ countries. The company’s success is built on its Everyday Low Prices (EDLP) strategy, supported by efficient supply chain management, data-driven decision-making, and large-scale operations across its three major segments — Walmart U.S., Walmart International, and Sam’s Club. As a global leader in retail and logistics innovation, Walmart leverages advanced analytics to optimize inventory, pricing, promotions, and demand forecasting. Analyzing its weekly sales data provides valuable insights into store performance, holiday effects, and economic influences, making it an ideal case for applying data science and predictive modeling to real-world business challenges.

## Project Overview
This project applies advanced time-series and machine learning techniques to Walmart’s weekly sales dataset to explore temporal trends, detect sales anomalies, and model the influence of macroeconomic factors. The goal is to generate accurate short-term forecasts and actionable insights that enhance business intelligence and strategic planning capabilities.

#### Key Objectives

The core goals of this analysis are to:

* Assess overall sales trends to determine whether consistent growth is occurring over time.

* Evaluate the effectiveness of Walmart’s sales strategies across multiple stores and regions.

* Identify top- and bottom-performing stores and weeks, highlighting patterns in geographic and temporal performance.

* Uncover the drivers of sales variability, including macroeconomic factors such as CPI, unemployment rate, fuel price, temperature, and holiday events.

* Build a forecasting models to predict future weekly sales and support data-driven decision-making.

* Deliver actionable insights and recommendations that enhance operational efficiency and optimize sales strategies.

### Analytical Objectives

* Sales Trend Analysis – Evaluate total and average weekly sales to detect patterns and growth trajectories.

* Holiday Impact Assessment – Quantify the influence of holiday weeks on sales performance using statistical tests.

* Outlier and Seasonality Detection – Identify anomalies and recurring sales cycles through visual analysis.

* External Driver Analysis – Examine correlations between sales and macroeconomic factors such as fuel prices, CPI, and unemployment.

* Forecasting Future Sales – Leverage time-series modeling to predict sales and visualize the sales trajectory.

* Strategic Insights & Recommendations – Summarize findings to inform data-driven business decisions.

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

The dataset includes the following variables:

| Column Name | Type | Description |
| :--- | :--- | :--- |
| Store | Int | Unique store identifier |
| Weekly_Sales | Float | Total sales for the week |
| Holiday_Flag | Int | Indicates whether the week contained a major holiday (1 = Yes, 0 = No) |
| Temperature | Float | Average temperature during the week |
| Fuel_Price | Float | Average fuel cost per gallon |
| CPI | Float | Price Index |
| Unemployment | Float | Unemployment rate for the corresponding region |


#### Data Preparation Steps

Checking for missing/null values and duplicates in the dataset for data integrity.

Data Type Conversion: Converted Date column to datetime format for accurate time-series indexing.

Outlier Detection & Visualization: Identified outliers using boxplots and the Interquartile Range (IQR) method to ensure robust statistical analysis.

Feature Formatting: Ensured consistent column naming, date sorting, and numerical scaling for modeling.

Time-Series Structuring: Set the Date column as the index to facilitate resampling, rolling averages, and forecasting models.

## Exploratory Data Analysis (EDA)

* How much total revenue does Walmart generate weekly, and what is the average weekly sales performance across all stores?

* How have total weekly sales changed over the entire period of the data? Are there consistent patterns, spikes, or dips?
  
* Which months typically show the highest and lowest sales?

* Do sales follow similar weekly patterns every year, or do some years perform better during certain periods?

* Is there an overall upward or downward trend across years?

* What is the distribution of weekly sales?

* Are there outliers that represent special events or data errors?

* What is the typical weekly sales performance across stores, and how does it vary?

* Which stores are driving the most revenue?

* Do holiday weeks significantly boost sales compared to regular weeks?

* Which months show the most significant holiday spikes?

* How do external economic factors such as fuel prices, CPI, and unemployment affect Walmart’s sales performance?

* Heatmap of correlations between Weekly Sales and all numeric variables.
  



#### Statistical Analysis



## Machine Learning 

* Which economic and environmental factors most influence weekly sales?
  
A regression model (Random Forest or XGBoost) was trained to predict weekly sales using external factors (CPI, Unemployment, Fuel price, Temperature).

Evaluation Metrics:

Mean Absolute Error (MAE)

Root Mean Squared Error (RMSE)

R² Score

Feature importance analysis revealed that:

Store, Holiday_Flag, and Unemployment were top predictors of weekly sales.

## Time Series Forecasting

To predict future sales, the dataset was transformed into a time series format. Models such as ARIMA, SARIMA & SARIMAX were evaluated to capture trends and seasonality.



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
| Programming | Description |
| :--- | :--- | 
| Python | Core programming language for data cleaning, transformation, and analysis. | 
| Pandas | Data wrangling and manipulation, handling missing values, and efficient group-by operations. | 
| NumPy | Numerical computing and support for vectorized operations. | 
| Matplotlib |  Creation of static, high-quality visualizations and custom plots. | 
| Seaborn | Advanced statistical graphics and aesthetically pleasing charts. | 
| Jupyter Notebook | Interactive environment for code execution, analysis, and visualization. | 
| Git & GitHub | Version control, project documentation, and public repository hosting. | 

### Models & Techniques

| Technique | Model/Tool |
| :--- | :--- |
| Statistical Analysis | Welch’s T-test, Correlation Analysis |
| Time-Series Forecasting |  ARIMA / SARIMA |
| Data Handling | Pandas, NumPy |
| Model Evaluation | RMSE, MAPE, and visual diagnostics |

##### About Dataset

| Attribute     | Description |
| :--- | :--- |
| **Dataset**    | Walmart Weekly Sales |
| **Source**     | [Kaggle – Walmart Sales Data](https://www.kaggle.com/datasets/mikhail1681/walmart-sales?select=Walmart_Sales.csv) |


















