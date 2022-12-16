# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 4a: West Nile Virus Prediction

## Notebooks
- Part 1: Data Cleaning
- Part 2: EDA, Visualisations, Modelling
- Part 3: Spray Analysis and Cost-Benefit Analysis

------

## Background
West Nile Virus(WNV) is most commonly spread to humans through infected mosquitoes. Around 20% of the people who become infected witht he virus develop symptoms ranging from a persistent fever, to serious neurological illnesses that can result in death. 

In 2002, the first human cases of the WNV were reported in Chicago. By 2004 the City of Chicago and the Chicago Department of Public Health(CDPH) had established a comprehensive surveilance and control program that is still in effect today. 

Due to the rising seasonal epidemic of the WNV in Chicago, an increasing number of people need medical attention. As such, there is a need for better mosquito control. However, the City of Chicago can only react to the new cases and spraying pesticide is costly and must be done regularly. 

------

## Problem Statement
#### Build a classification model of at least 90% recall score to predict areas of the city where there are mosquitoes carrying the West Nile Virus. Optimise current mosquito control measures to effectively and efficiently tackle the mosquito problem and create a desirable cost-benefit analysis. 

------

## Target Audience
- Members of the Chicago Department of Public Health (CDPH)

------

## Data sources
### Data Provided
* [Kaggle West Nile Virus](https://www.kaggle.com/competitions/predict-west-nile-virus/data)

------

## Additional sources
* [Culex Mosquitoes](https://www.mdpi.com/2075-4450/13/9/758)
* [How to get rid of mosquitoes without killing friendly pollinators](https://www.washingtonpost.com/home/2022/07/06/mosquito-sprays-harm-pollinators/)
* [West Nile Virus Transmission](https://www.cdc.gov/westnile/transmission/index.html)

------
## Data Dictionary
#### Dataset name: train 
##### This contains data provided by source to be used in the project.
|Feature|Type|Description|
|---|---|---|
|Date|Object|Date that the WNV test was performed|
|Address|Object|Approximate address of the location of the trap|
|Species|Object|The species of the mosquitoes found in trap|
|Block|Int|Bloack number of the address|
|Street|Object|Street name|
|Trap|Object|ID of the trap|
|AddressNumberAndStreet|Object|Approximate address of the location of trap|
|Latitude||Float|Latitude of trap|
|Longitude|Float|Longitude of trap|
|AddressAccuracy|Int|Accuracy of the address|
|NumMosquitos|Int|Number of mosquitoes caught in trap|
|WnvPresent|Int|Whether the WNV was present in the mosquitoes caught in trap. 1 indicates WNV is present. 0 indicates WNV is not present|

#### Dataset name: test 
##### This contains data provided by source to be used in the Kaggle challenge.
|Feature|Type|Description|
|---|---|---|
|Date|Object|Date that the WNV test was performed|
|Address|Object|Approximate address of the location of the trap|
|Species|Object|The species of the mosquitoes found in trap|
|Block|Int|Bloack number of the address|
|Street|Object|Street name|
|Trap|Object|ID of the trap|
|AddressNumberAndStreet|Object|Approximate address of the location of trap|
|Latitude||Float|Latitude of trap|
|Longitude|Float|Longitude of trap|
|AddressAccuracy|Int|Accuracy of the address|

#### Dataset name: spray
##### This contains data of spraying of pesticides conducted by the City of Chicago.
|Feature|Type|Description|
|---|---|---|
|Date|Object|Date the spraying was conducted|
|Time|Object|Time of the spraying|
|Latitude|Int|Latitude of the location of spraying|
|Longitude|Int|Longitude of the location of spraying|

#### Dataset name: weather 
##### This contains data of the weather conditions of the City of Chicago.
|Feature|Type|Description|
|---|---|---|
|Station|Int|The station that the weather was recorded from|
|Date|Object|Date the weather was recorded|
|Tmax|Int|Highest temperature recorded|
|Tmin|Int|Lowest temperature recorded|
|Tavg|Object|Average temperature recorded|
|Depart|Object|
|DewPoint|Int|
|WetBulb|Object|
|Heat|Object|
|Cool|Object|
|Sunrise|Object|
|Sunset|Object|
|CodeSum|Object|
|Depth|Object|
|Water1|Object|
|SnowFall|Object|
|PrecipTotal|Object|
|StnPressure|Object|
|SeaLevel|Object|
|ResultSpeed|Float|
|ResultDir|Int|
|AvgSpeed|Object|


#### Data features used in modelling
|Feature|Type|Dataset|Description|
|---|---|---|---|
|Address_w|Float|trap_trn_weather_full|The weight assigned to address location based on the likelihood of wnv|
|Month_w|Float|trap_trn_weather_full|The weight assigned to month based on the likelihood of wnv|
|Species_w|Float|trap_trn_weather_full|The weight assigned to mosquito species based on the likelihood of wnv|
|DewPoint_14daysavg|Float|trap_trn_weather_full|The average DewPoint temperature of the past 14 days (units in Fahrenheit)|
|WetBulb_14daysavg|Float|trap_trn_weather_full|The average WetBulb temperature of the past 14 days (units in Fahrenheit)|
|Tavg_14daysavg|Float|trap_trn_weather_full|The average daily temperature of the past 14 days (units in Fahrenheit)|
|Cool_14daysavg|Float|trap_trn_weather_full|The average cooling temperature of the past 14 days (units in Fahrenheit)|
|ResultSpeed_14daysavg|Float|trap_trn_weather_full|The average resultant wind speed of the past 14 days (units in MPH)|
|AvgSpeed_14daysavg|Float|trap_trn_weather_full|The average daily wind speed of the past 14 days (units in MPH)|
|PrecipTotal_14daysavg|Float|trap_trn_weather_full|The average of the total precipitation of the past 14 days (units in inches)|
|r_humidity_14daysavg|Float|trap_trn_weather_full|The average relative humidity of the past 14 days (units in percentage)|
|WnvPresent|Int|trap_trn_weather_full|Label for presence of west nile virus in mosquito (0 indicates the absence of wvn and 1 indicates the presence of wnv)|


------
### Key takeaways:
1. Only 2 of the 6 mosquito species carry the virus.
2. Recall score was important to accurate identify the virus.
3. Adaptive Boosting Classifier returned the best recall score of 96%.
4. Spraying can be optimised with 11% benefit returns.


------
### Next Steps, Recommendations, Conclusion
#### Moving forward
There were irregularity in data collection. The data collected from the traps with irregular across the months and not all traps were recorded each time. This did not allow the team to determine trends in data or it was insufficient to draw correlation between other features. 

The data was very imbalanced with 95% of the total recorded mosquitoes to be negative of the virus. Resampling of the data had to be done as the model needs to be able to identify mosquitoes positive of the virus. By having more data on mosquitoes postitive to the virus it would definitely help to increase model accuracy.  

More supporting data will be needed. Such data includes natural disasters, such as flooding, population density, and construction sites. Chicago had multiple floods during the duration that the data was recorded. Floods and construction sites are prone to leave pools of stagnant water which is a definitive breeding ground for mosquitoes. Such data will the team to draw trends across the years and it may explain fluctuations found during analysis.  

#### Recommendations


#### Conclusion


------
