# Walmart Sales Analysis & Forecasting
![Walmart_Logo](https://upload.wikimedia.org/wikipedia/commons/b/b1/Walmart_logo_%282008%29.svg)

# Introduction 
**Walmart Inc.**, founded in 1962 by Sam Walton and headquartered in Bentonville, Arkansas, is the world’s largest retail corporation, operating over 10,000 stores and serving more than 230 million customers weekly across 20+ countries. The company’s success is built on its Everyday Low Prices (EDLP) strategy, supported by efficient supply chain management, data-driven decision-making, and large-scale operations across its three major segments — Walmart U.S., Walmart International, and Sam’s Club. As a global leader in retail and logistics innovation, Walmart leverages advanced analytics to optimize inventory, pricing, promotions, and demand forecasting. Analyzing its weekly sales data provides valuable insights into store performance, holiday effects, and economic influences, making it an ideal case for applying data science and predictive modeling to real-world business challenges.

### Project Overview

This project explores **Walmart’s weekly sales data** to uncover key performance drivers, assess the impact of holidays and economic conditions, and forecast future sales using **time-series modeling (ARIMA, SARIMA, SARIMAX)**.  

Through a combination of **Exploratory Data Analysis (EDA)**, **statistical inference**, and **forecasting techniques**, this analysis provides both **explanatory** and **predictive insights** into Walmart’s sales performance.

 ### Project Goals

- Assess overall sales trends and performance consistency across time.
- Identify **top-performing stores** and high-revenue periods.
- Evaluate the **impact of holidays and external economic factors** (CPI, unemployment, fuel prices).
- Develop predictive models to **forecast future sales** and support strategic decision-making.
- Derive **data-driven recommendations** for optimizing operations and planning.

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

Are there any anomalies or extreme values that distort average performance?

![Outliers](https://github.com/damoncaliber/Walmart-Sales-Analysis-Forecasting/blob/main/Images/outliers.png)

Boxplots reveals clear outliers around holiday periods — primarily in November and December.

These are genuine event-based spikes, not data errors, reflecting true consumer behavior.

Removing them would distort the model, so they were retained for accurate seasonal pattern recognition.

#### Overall Sales Performance

Walmart generated a total of $6.73 billion across all stores.

The average weekly sales per store stood at $1.05 million, showing a stable baseline performance.

![Trend_over_time](https://github.com/damoncaliber/Walmart-Sales-Analysis-Forecasting/blob/main/Images/Weekly_sales_trend.png)

The time-series line plot displays regular repeating patterns every year, with prominent spikes in the final quarter (November–December).

The pattern’s consistency implies reliable seasonality, ideal for time-series forecasting.

No structural decline is observed, suggesting sustained demand stability across years.

This establishes Walmart’s core sales rhythm — consistent weekly flow with holiday-driven peaks.
It sets a benchmark for later analyses like seasonality, store performance, and forecasting.
  

* Do monthly sales follow a recurring seasonal pattern year over year?

![Month_by_years](https://github.com/damoncaliber/Walmart-Sales-Analysis-Forecasting/blob/main/Images/month_by_years.png)


![Monthly_trend](https://github.com/damoncaliber/Walmart-Sales-Analysis-Forecasting/blob/main/Images/monthly_sales_trend.png)

December outperformed all months, aligning with the holiday shopping rush.

February and May were the lowest-performing months, marking post-holiday and pre-summer slowdowns.

The difference between top and bottom months reached nearly 40%, confirming seasonal elasticity in customer demand.

This monthly pattern highlights Walmart’s reliance on major holiday cycles — essential for inventory and marketing optimization strategies.

![Trend_with_holiday](https://github.com/damoncaliber/Walmart-Sales-Analysis-Forecasting/blob/main/Images/holiday_trend.png)

Time series with holiday weeks highlighted or colored differently.
Visual confirms recurring strong spikes during holiday windows; comparison of pre- and post-holiday weeks can reveal carryover or stockout effects.


*  Which months show the most significant holiday spikes?

![Holiday_by_month](https://github.com/damoncaliber/Walmart-Sales-Analysis-Forecasting/blob/main/Images/Holiday_by_month.png)

* Which stores are driving revenue, and how does performance vary across locations?
  

Top 5 stores by average sales

![Top_5](https://github.com/damoncaliber/Walmart-Sales-Analysis-Forecasting/blob/main/Images/Top_5_performing.png)

These stores are high-impact revenue centers — often the best candidates for pilot programs, premium product placements, or increased marketing spend. Their share of total sales quantifies concentration risk.

Prioritize these locations for new initiatives; ensure supply chain prioritization during peak windows.

Do holiday weeks significantly boost sales compared to non-holiday weeks?

![Holiday_Non-Holiday](https://github.com/damoncaliber/Walmart-Sales-Analysis-Forecasting/blob/main/Images/Holidays_vs_NonHoliday.png)

Holiday weeks show a substantial sales increase, with weekly averages nearly double that of non-holiday weeks.

A t-test (p < 0.05) confirmed a statistically significant difference between the two groups.

The strongest spikes correspond to Thanksgiving, Black Friday, and Christmas periods.

Holiday-driven events are key profit accelerators.

Walmart should strategically allocate higher stock levels, staff, and marketing during these weeks to maximize returns.

* What is the typical weekly sales performance across stores, and how does it vary?
  
![Weekly_store](https://github.com/damoncaliber/Walmart-Sales-Analysis-Forecasting/blob/main/Images/ave_weekly_store_perf.png)

A small set of stores contributes a disproportionately large share of total sales; sales volatility distinguishes steady performers from promotion-driven stores. 

Ranking stores by average and volatility helps categorize them into stable/high-volume, high-variance/seasonal, and low-volume segments.

Benchmark operations and staffing against top stores; for volatile stores, consider targeted promotions or inventory safety buffers.

Create three clusters (stable-high, unstable-high, low) and run root-cause analysis per cluster (demographics, competition, store-size).

Stores were ranked by average weekly sales; Store 20, Store 4, and Store 14 emerged as top performers.

Variability in sales across stores suggests different regional market strengths and operational capacities.

The sales distribution emphasizes Walmart’s need for regionalized demand forecasting and localized strategies rather than a one-size-fits-all approach.

* Which stores are underperforming?

![Bottom_5](https://github.com/damoncaliber/Walmart-Sales-Analysis-Forecasting/blob/main/Images/bottom_5.png)

Lower-performing stores showed inconsistent patterns, possibly due to smaller population coverage or limited product lines.

* How do macroeconomic indicators like fuel price, CPI, and Unemployment affect sales?


![Economic_indictators](https://github.com/damoncaliber/Walmart-Sales-Analysis-Forecasting/blob/main/Images/Economic_factors_heat.png)

Correlation heatmaps reveals:

Negative correlation between sales and unemployment rate.

Slight inverse correlation with fuel prices — higher costs may limit in-store visits.

Weak positive correlation with CPI, suggesting stable demand amid price changes.

Macroeconomic conditions modestly affect Walmart’s performance — indicating strong resilience, but also sensitivity to economic downturns.

## Machine Learning 

Regression Analysis — Drivers of Sales

Objective:
To identify which factors have the most influence on weekly sales across Walmart stores.

Approach:
A Multiple Linear Regression model was trained using the following predictors:

Holiday_Flag (holiday vs. non-holiday weeks)

Temperature

Fuel_Price

CPI (Consumer Price Index)

Unemployment

![Regression_analysis](https://github.com/damoncaliber/Walmart-Sales-Analysis-Forecasting/blob/main/Images/Importance_score.png)

Key Findings:

Unemployment showed a negative effect, suggesting weaker sales when joblessness rises.

Temperature and Fuel price had smaller but notable impacts, indicating seasonal and economic sensitivity.

Overall model performance **(R² ≈ 0.72)** indicated that these factors explain a substantial portion of sales variation.

Macroeconomic and seasonal drivers jointly influence weekly sales patterns — holidays being the most dominant factor.

## Time Series Forecasting

Objective:
To predict future weekly sales trends using models that account for seasonality, trend, and exogenous economic variables.

![Best_model](https://github.com/damoncaliber/Walmart-Sales-Analysis-Forecasting/blob/main/Images/best_model.png)

**Best Model:** `SARIMA` (lowest MAE & RMSE)

| Model | Description | Strength | Weakness | Performance |
|:------|:-------------|:----------|:-----------|:-------------|
| **ARIMA** | Captures trend and autocorrelation | Simple baseline | Misses seasonality | Moderate |
| **SARIMA** | Models seasonal trends | Captures weekly/annual cycles | Lacks external context | Best |
| **SARIMAX** | Includes economic variables (CPI, Fuel, Unemployment) | Best real-world performance | More complex tuning | Better  |

![sarima_model](https://github.com/damoncaliber/Walmart-Sales-Analysis-Forecasting/blob/main/Images/sarima_model.png)

**Forecast Insights:**

- Projected **steady sales growth** with **predictable holiday peaks**
  
- Accurate short-term forecasting suitable for **demand planning** and **inventory optimization**.

## Key Findings & Recommendations

Analytical Insights from EDA

Through detailed EDA, several important trends and patterns were revealed:

#### Seasonality & Peak Trends:
Sales displayed a consistent seasonal pattern, with sharp spikes during November and December — coinciding with major U.S. holidays such as Thanksgiving and Christmas. These periods significantly outperformed non-holiday months, confirming seasonal consumer behavior as a core driver of performance.

#### Store-Level Variation:
Not all Walmart stores contributed equally to total sales. A small subset of stores accounted for a disproportionately large share of revenue, reflecting store-level heterogeneity in location, demographics, and operational efficiency.

#### Holiday vs. Non-Holiday Performance:
A Welch’s t-test confirmed a statistically significant difference in sales between holiday and non-holiday weeks (p < 0.05), supporting the hypothesis that holiday promotions and events drive measurable sales lifts.

#### Economic Sensitivity:
Correlation analysis showed that CPI (inflation indicator) and Unemployment were inversely related to sales. Higher unemployment and inflation were associated with lower weekly sales, suggesting consumer purchasing power plays a critical role in Walmart’s performance.

#### Fuel Price Dynamics:
Fuel prices had a mild negative relationship with sales — implying that higher fuel costs might slightly discourage in-store shopping or reduce overall spending capacity.

These insights provided the foundation for selecting the exogenous variables later used in forecasting models (SARIMAX).

The linear regression model achieved an R² of ~0.72, suggesting that these predictors collectively explain most of the variability in weekly sales.

This confirmed that Walmart’s sales performance is not random — but systematically influenced by a mix of seasonal, economic, and operational factors.

#### Forecast Outcome:
The SARIMA model projected steady sales growth with periodic holiday peaks and minimal volatility. It effectively captured real-world economic conditions, enabling more realistic business planning.

The model’s accuracy and well-behaved residuals indicate strong generalization — meaning it can be confidently used for operational forecasting and scenario testing.

#### Recommendations

1. **Automate Forecasting Pipelines**  
   Implement SARIMAX-based models for real-time sales prediction and inventory management.

2. **Enhance Q4 Readiness**  
   Allocate more resources for **holiday periods**, where sales are consistently highest.

3. **Monitor Economic Indicators**  
   Track **CPI and unemployment** to proactively adapt pricing and promotions.

4. **Store Performance Benchmarking**  
   Identify best-performing stores and **replicate successful operational strategies** network-wide.

5. **Data-Driven Decision Support**  
   Integrate forecasting outputs into **strategic dashboards** for planning and resource allocation.


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
| Time-Series Forecasting |  ARIMA / SARIMA / SARIMAX |
| Data Handling | Pandas, NumPy |
| Model Evaluation | RMSE, MAPE, and visual diagnostics |

##### About Dataset

| Attribute     | Description |
| :--- | :--- |
| **Dataset**    | Walmart Weekly Sales |
| **Source**     | [Kaggle – Walmart Sales Data](https://www.kaggle.com/datasets/mikhail1681/walmart-sales?select=Walmart_Sales.csv) |


















