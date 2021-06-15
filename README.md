![image](https://github.com/sgautam666/Time_Series_Forecasting_of_Solar_Irradiance/blob/main/images/_1080px_landscape.jpg)

# Time Series Forecasting of Solar Irradiance

**Author**: [Suman Gautam](mailto:smngeo@gmail.com)

## Overview

There is a rapid growth in solar energy generation for state of Texas
According to EIA, Texas planned to add 10 gigawatts (GW) of utility-scale solar capacity by the end of 2022

Managing power generation and distribution requires use of accurate forecast of energy generation across different sources
With increase in Solar power generation, forecast of solar energy generation would be critical to maintain power distribution and reduce short term power outage 
A multi-scale solar irradiance forecasting may help to estimate the net solar energy generation.


## Project Summary

This project is aimed to generate a predictive modelling algorithm that can forecast solar irradiance on short-term (hourly) to medium long term (10 - 30 days). 

## Data

The for this project was acquired from Daily [NOAA](https://gml.noaa.gov/aftp/data/radiation/surfrad/) that hosts Surface Radiation data from 7 station around the United States ![image](https://github.com/sgautam666/Time_Series_Forecasting_of_Solar_Irradiance/blob/main/images/location_map.png). The data are avilalble in the interval of ~17s of daily records. Although, there is yearly data going back few years, the primary focus of this focus is to predict on the short-term basis. Therefore, only data from year 2020-2021 was used for this project. The 2020 data was used as training data whereas the 2021 data was used for validation and test, since the 2021 data as of current is incomplete. 

## Data Exploration

The size of data is huge as it records data at ~17s interval. Because we are interested in forecasting in hours and/or day to day basis, the data will be downsampled to hours only. The full data exploration notebook can be found in [Data Exploration](./Surfrad_data_collection.ipynb). Though, there are multitude of features available for this dataset, for this project only one feature that is associated with solar energy is used. In this case, 'Netsolar' radiation will be our time series upon which all the forecasting methods will be tested.

## Modelling 
In this project, two different kinds of modelling approach were experimented: 
1. classical time series method such as ARIMA and SARIMAX:[Modelling_I](./Modelling_Sarimax.ipynb).
2. Neural Network Architecture such as LSTM : [Modelling_II](./LSTM_Modelling_All_Location.ipynb).

Initial time series analysis indicated presence of seasonality in the data. However, SARIMAX method which accounts for seasonality doesn't seems to forecast as expected. This could be related to the lack of more historic data. On the otherhad, LSTM network seems to perform much better on this datata ![Image](https://github.com/sgautam666/Time_Series_Forecasting_of_Solar_Irradiance/blob/main/images/Training%20Prediction.png).

## Results

Time Series forecasting was performed on 24 hr, 10 days and 30 days interval. In general, the model tends to forecast better in the short term as can be seen in the result ![Image](https://github.com/sgautam666/Time_Series_Forecasting_of_Solar_Irradiance/blob/main/images/24hr_days_forecast.png). For long term forecast, the model doesnt perform better beyond 10 days and the performace is satisfactory upto 10 days forecasting period ![Image](https://github.com/sgautam666/Time_Series_Forecasting_of_Solar_Irradiance/blob/main/images/10_days_forecast.png)

Several consistent drop in solar irradiance is observed across many stations. However, the irradiance pattern seems to be cyclical, with highest value during the summer and lowest around January – March.


## Action Items
During the 2021 power outage in Texas, which was around February 7 to February 18, Solar Irradiance was also lowest. If this pattern is cyclical, our model can predict the next occurrence of decreased solar irradiance, and thus alerting power generation company to plan ahead of the power generation and alternatives in case of disaster related to snowstorm. 

Apart from global irradiance highs and lows, several consistent drop in the irradiance patterns have been noticed. It is suggested to collect past historic data to make a better comparison of such significant drops.

The model can be used immediately to predict solar condition within windows of a day, and thus plan the electricity generation smoothly

##  Future Recommendations
Current dataset of 1 year period was originally used to predict short-term irradiance. However, the cyclical behavior of the solar irradiance can be useful in predicting long term and therefore more historic data is needed.

Current scope of work only allowed for univariate analysis, however there is a plenty of extra features that are available and are highly correlated to the solar irradiation. A multivariate method will be advantageous in creating accurate forecast.

## For More Information

See the full analysis in the [Jupyter Notebook](./final_model.ipynb) or review this [presentation]().



## Repository Structure

```
├── data
├── images
├── Apple-Twitter-Senweeted-DFE.csv
├── Brand_Sentiment_Analysis_Final.ipynb
├── Brand_Sentiment_Analysis_Notebook.pdf
├── Brand_Sentiment_Analysis_ppt
├── Miscellaneous_files
└── README.md
```