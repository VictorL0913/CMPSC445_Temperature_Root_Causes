# CMPSC445 Project 1 Global Temperature Root Cause

Google Colab Link: [Notebook](https://colab.research.google.com/drive/1Mb3mG1ULvBhhhoPoH7N6IVBTdtKqTDnY?usp=sharing)

### Project Overview
Build a regression‑based analytical pipeline to identify the most influential drivers (“root causes”) of global temperature change.
Students will collect data from multiple scientific data sources, merge them into a single dataset, train regression models, and use feature importance to determine which environmental factors contribute most to temperature variation.

### Assignment Tasks
The goal of the project was to build a regression-based analytical pipeline to find the most influential factor of global temperature change. I collected data from multiple science sources like NOAA, NASA, and OWID that included atmospheric greenhouse gases and NASA global temperature anomalies. The datasets were cleaned, merged, and processed to create predictive models. Feature importance from regression models was used to find which factor was most influential to temperature change. 

### Temperature Root Cause
To determine the primary factors in global temperature anomalies, I analyzed the effects of three major greenhouse gases:
- CO2 (Carbon Dioxide)- measured in ppm
- CH4 (Methane) - measured in ppb
- N2O (Nitrous Oxide) - measured in ppm

Additionally, I added __"Years Since 1958"__ colum to get the overall long-term trend in global temperature to account for the increase in temperature over the decades, which also captures time trend. I also used __5 year moving average__ of greenhouse gas levels to reduce noise that can be caused by yearly variations or unusual spikes to allow model to better detect the long-term relationship between temperature and greenhouse gases. This helps the regression models to focus on patterns and not temporary fluctuations to improve accuracy and interpretability.

### Description of Methods
#### Data Collection and Cleaning
- Collected motnhly and yearly datasets for 3 major greenhouse gases -- CO2, CH4, N2O --along with global temperature anomaly. Dara were obtained from NASA, NOAA, and OWID  scientific sources to get a broad coverage.
- To prepare the data:
  - __Aggregation__: Monthly measurements were aggregated to yearly averages to reduce noise and align datasets
  - __Merging__: Datasets were merged using the __'year'__ column as a key to create an unified dataset that contained the greenhouse gases, temperature anomalies, and country information.
  - __Handling Missing Data__: Missing values were first interpolated linearly to get values based on neighboring years, and remaining missing values were dropped.
  - Total samples: 4320
#### Feature Engineering
- To help the model better capture the long term climate trends and relationships, feature engineering was used to create new features:
  1. __Years Since 1958__: represent number of years since 1958 to get long term temperature trends; allows model to distinguish between temporary fluctuations and steady increases in temperature.
  2. __5-Year Rolling Averages__: rolling averages for greenhouse gases were computed using global data; used to reduce noise form seasonal events, and highlight long term trends that are more relevant to global temperature changes.
- Using these featuers, the model can get a better understanding of the relationship between greenhouse gases and gloval temperature changes, which will improve interpretability and predictive accuracy.
#### Example Data After Preprocessing
![alt text](https://github.com/VictorL0913/CMPSC445_Temperature_Root_Causes/blob/main/Graphs/climate_dataset.png)

#### Model
##### Linear Regression Model
- Captures linear relationship between temperature anomaly and greenhouse gases.
- Provides interpretable coefficients that inidcate the strength and direct of each feature's impact.

##### Random Forest Regressor
- Captures complex and non-linear relations between features that may not be apparent in a linear model.
- Provides feature importance scores that help identify which features are the most influential in global temperature changes.
  
#### Visualization
To interpret the results, these plots were created:
- __Scatter plot__: visualize the relationship between temperature changes and individual greenhouse gases
- __Time Series plot__: comared global temperature anomalies and greenhouse gases over time to show long-term trends and patterns
- __Feature Importance Chart__: show the influence of each feature according to the __Random Forest__ model.
### Performance Evaluation
- __Linear Regression__
  - R2 score: 0.89
 
| Feature             | Coefficient |
|--------------------|------------|
| N2O_global_5yr_avg | 7.81       |
| YearsSince1958      | -3.99      |
| N2O                 | -2.43      |
| CH4_global_5yr_avg  | -1.52      |
| CH4                 | 0.30       |
| CO2                 | -0.27      |
| CO2_global_5yr_avg  | 0.25       |

The linear regression model achieved a R2 score around 0.89, which shows that it explains most of the variance in global temperature anomalies. The strongest indicator was the 5 year rolling average of N2O which shows the importance of the long term trends for N2O. With that being said, other features like CO2 and CH4 might have had smaller contributions due to correlations between variables.

- __Random Forest__
  - R2 score: 1.0

| Feature              | Importance |
|---------------------|-----------|
| N2O_global_5yr_avg   | 0.166     |
| CO2                  | 0.165     |
| N2O                  | 0.147     |
| YearsSince1958       | 0.147     |
| CH4                  | 0.138     |
| CH4_global_5yr_avg   | 0.127     |
| CO2_global_5yr_avg   | 0.110     |

The Random Forest model achieved a R2 score of 1.0, which shows that it was able to capture all variability in the dat. Feature importance shows N20 and CO2 as the most influential drivers of temperature anomalies. The model captures nonlinear relationships and interations that linear regression might have missed, but the perfect R2 score might also indicate overfitting that could have been caused by correlated features. 

#### Graphs

![alt text](https://github.com/VictorL0913/CMPSC445_Temperature_Root_Causes/blob/main/Graphs/Random_Forest_importance.png) 
![alt text](https://github.com/VictorL0913/CMPSC445_Temperature_Root_Causes/blob/main/Graphs/temperature_anamoly_ghg.png)
![alt text](https://github.com/VictorL0913/CMPSC445_Temperature_Root_Causes/blob/main/Graphs/time_series.png) 

### Conclusion
The project analyzed temperature anomalies using regression models to identify major drivers in climate change. Both linear regression and random forest models indicate that N2O and CO2 were the primary contributors in rising global temperature with N2O (5 year rolling average) showing the strongest influence. However, ther are sevel limiatations that this project shows. The dataset only includes anthropogenic greenhouse gases and temperature anomalies, but does not inlcude natural factos such as solar irradiance, volcanix activity, and oceanic cycles, which can also influence gloval temperatures. The random forest model also achieved a perfect 1.0 R2 score, which indicates overfitting which could be due to high correlation between features. For improvements in the future, the project could include other variables like solar irradiance, volcanic activity, and oceanic cycles. Another improvement would be using regularization or cross validation to address overfitting issues that was presented in the evaluation. Overall the results showed that long-term greenhouse gas trends are major factors in global temperature anomalies, while also showing the importance of broader climate coverage and model evaluation for climate analysis. 
### AI usage
AI tools were usd to assist with feature engineering and visualization including:
- formatting and improving visual clarity for plots
- help with adjusting errors with rolling averages
