# Power-Outage-Analysis
**By:** David Chhuon-Chan

## Introduction
This project will analyze a dataset of major power outages that happened in the United States in order to understand patterns in outage duration and reporting. In particular, I'm exploring factors related to outage characteristics, test for missingness mechanisms, and build a predictive model for outage duration. 

The goal is to determine which features are helpful for predicting power outage duration.
## Data Cleaning and Exploratory Data Analysis
The dataset contains imformation on major power outages across the U.S., which each row representing a power outage.
The raw data of power outages was cleaned to be easier to work with. Some irrelevant columns were dropped and an 'OUTAGE.DURATION' column was created for easier data handling.
Some relevant columns are:
- **'OUTAGE.DURATION'**: The amount of time of each outage in minutes.
- **'CAUSE.CATEGORY'**: A category describing the cause of the outage.
- **'CUSTOMERS.AFFECTED'**: The number of customers affected by the power outage.
- **'CLIMATE.REGION'**: The type of climate region where the power outage happened.
<img width="1285" height="246" alt="image" src="https://github.com/user-attachments/assets/8428ae94-87ea-4537-90b8-26c3059aaafe" />
This univariate graph shows outages by cause category and each category's frequency. From this graph, we can see that 'severe weather' caused the most power outages.
<img width="928" height="603" alt="image" src="https://github.com/user-attachments/assets/ab5ae293-1b0e-4502-af8c-49d14171bb14" />
This bivariate plot shows the outage duration plotted vs month.
<img width="926" height="558" alt="image" src="https://github.com/user-attachments/assets/1018cb1e-d811-4f01-9f09-73617685ca1a" />
## Assessment of Missingness
I believe there are potentially a few columns in the dataset that are NMAR. One of these columns is the OUTAGE.DURATION column. I believe it could be NMAR 
## Hypothesis Testing
I ran two hypothesis tests.

The first hypothesis test had to do with outage duration and what it was caused by.
Null Hypothesis: Outages have the same outage duration regardless of if it was caused by weather or not.
Alternative Hypothesis: Outages caused by weather are longer than non weather caused outages.
P-Value: 0.0
Conclusion: With a p-value of 0.0 I reject the null hypothesis as it shows that outages caused by weather on average are longer.

My second hypothesis test had to do with outage duration and region.
Null Hypothesis: Outage duration is the same regardless of region.
Alternative Hypothesis: The outage duration in one or more climate regions is higher than others.
P-Value: 0.0332
Conclusion: I reject the null hypothesis as the p-value shows that some climate regions have longer outage durations.

These questions were important because they help identify whether outage duration varies with external factors or by random variation. Understanding these relationships provides inside into which types of outages can be more severe and which regions are more vulnerable to power outages.
## Framing a Prediction Problem
My goal with this project is to be able to predict the duration of a power outage, making this a regression problem. The repsonse variable is **OUTAGE.DURATION**, which measures the length of outages in minutes. I chose this as the response variable because the outage duration is a meaningful measure of outage severity.

I'll be evaluating model performance using Root Mean Squared Error (RMSE). I chose RMSE because it measures the average magnitude of prediction error. 
## Baseline Model
I built a baseline linear regression model in order to predict power outage duration. It used two categorical features and applied one hot encoding betfore fitting into a linear regression.

**Features Used**
- **CLIMATE.REGION**: Nominal variable showing the climate region where the power outage happened
- **CAUSE.CATEGORY**: Nominal variable showing the cause of the power outage

This model could use some work as there's a bit of a gap between the trained RMSE and the test RMSE. The trained RMSE measured 4803.78 whereas the test RMSE measured at 7029.52.
## Final Model
To improve on the baseline model, I added a few new features.
**CUSTOMERS.AFFECTED**
**CAUSE.CATEGORY.DETAIL**
**PCT_WATER_TOT**
## Fairness Analysis
