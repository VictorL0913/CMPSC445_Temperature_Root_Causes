# CMPSC445 Project 1 Global Temperature Root Cause

Google Colab Link: [https://colab.research.google.com/drive/1Mb3mG1ULvBhhhoPoH7N6IVBTdtKqTDnY?usp=sharing]

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
#### Feature Engineering
#### Model
#### Visualization
#### Example Data After Preprocessing
![alt text](https://github.com/VictorL0913/CMPSC445_Temperature_Root_Causes/blob/main/Graphs/climate_dataset.png)

### Performance Evaluation

#### Graphs

![alt text](https://github.com/VictorL0913/CMPSC445_Temperature_Root_Causes/blob/main/Graphs/Random_Forest_importance.png) 
![alt text](https://github.com/VictorL0913/CMPSC445_Temperature_Root_Causes/blob/main/Graphs/temperature_anamoly_ghg.png)
![alt text](https://github.com/VictorL0913/CMPSC445_Temperature_Root_Causes/blob/main/Graphs/time_series.png) 

### Conclusion

### AI usage
