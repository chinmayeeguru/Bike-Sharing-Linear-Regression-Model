# INTRODUCTION

This case study aims to give an idea of applying linear regression in a real business scenario for a bike-sharing provider "BoomBikes" to model the demand for shared bikes with the available independent variables. It will be used by the management to understand how exactly the demands vary with different features. They can accordingly manipulate the business strategy to meet the demand levels and meet the customer's expectations. Further, the model will be a good way for management to understand the demand dynamics of a new market. 

# DATA EXPLORATION AND CLEANING

- In the data set we had few columns which did not contribute towards business goal and thus could be ignored for our analysis. Such columns were instant, dteday, casual and registered. We have dropped these columns.
- There were few categorical columns in this data set which hold the values in numerical form. Those were converted to their respective categorical form as per the data dictionary for better representation and understanding of data. 
- It was assumed that 0 - 6 represent Sunday - Saturday.

# EDA AND DATA VISUALIZATION

In this step we visualized and explored the categorical as well as continuous variables present in the data set.

![image](https://user-images.githubusercontent.com/103338455/162635165-22dd4e82-6ac2-481c-bc56-32d5cf46809b.png)

- Most of the days have temperature 10-30 degrees. T
- Distribution of temp and atemp are almost similar.
- Most of the days are with humidity 50-80.
- Wind speed seems to be distributed mostly between 5 - 20.
- Total count of rental bikes seems to be normally distributed with a mean value between 4000-5000.

![image](https://user-images.githubusercontent.com/103338455/162635229-e7613e93-8c8c-45ab-88d8-b58351c2ec94.png)

- There are no significant outliers as such present in the data
- Weather is surely impacting the bike rental counts as clearly visible from the plot. The meadin value is highest when the weather is good and then decreasing as the weather becomes worse.
- Season is also a fairly contributing factor in the total rental count. Summer and Fall are more favourable seasons.
- Working day seems to have a very little impact.
- More bikes are rented between the months Jun-Oct.
- Most of the days are good or fair weather days.
- Demand seems to be less on holidays.

![image](https://user-images.githubusercontent.com/103338455/162635270-5bf1bc53-3182-477f-a0e4-8a24ba5e8640.png)

- Most of the days in Fall season were good with clear sky followed by Summer, Spring and Winter.
- Winter has most number of bad weather days.

![image](https://user-images.githubusercontent.com/103338455/162635299-8f5b5514-4953-4639-b9ed-814d9a4eee52.png)

- Most of the days in the month of June, July, August and November are good weather days.
- October has the most number of bad weather days with heavy shower/snow.

![image](https://user-images.githubusercontent.com/103338455/162635316-bd3a3741-4ebd-4f1e-8dee-6d4ddbe376d7.png)

- Rental count was the highest in the Fall season irrespective of the weather condition.
- Spring season has the lowest demand.

![image](https://user-images.githubusercontent.com/103338455/162635350-79c65023-c59a-4927-8090-012db75b4423.png)

- In most of the months if weather is good/fair, demand is more.
- In July, irrespective of the weather condition, demand is high.
- The demand is the lowest in the month of January.

![image](https://user-images.githubusercontent.com/103338455/162635373-b3bbcce3-8861-4517-bf66-fba8e7337294.png)

Looks like holidays have less demand.

![image](https://user-images.githubusercontent.com/103338455/162635386-d8649ce2-1b22-42d5-96ce-3a2f759f26e0.png)

- Temperature and rental count are highly correlated.
- The demand is high on good weather days and when temperature is pleasant (20-30 degree).

![image](https://user-images.githubusercontent.com/103338455/162635407-e6365348-91a7-4290-8933-040d72517c11.png)

- Humidity and rental count are negatively correlated.
- The demand is high on good weather days when humidity is low (40-60).

![image](https://user-images.githubusercontent.com/103338455/162635438-74c0490f-b751-4a58-a637-333e10a72d02.png)

'temp' and 'atemp' are highly correlated, which means their impact on the total rental counts are fairly similar. Hence, we may consider just one (say temp) and ignore the other one while building our model to avoid any multicollinearity.

![image](https://user-images.githubusercontent.com/103338455/162635474-742699de-ed5e-43f7-a511-266f3ed7df52.png)

- 'temp' and 'atemp' are very highly correlated. If both present, they might introduce multicollinearity. Hence, we need to keep any one and drop the other one as they both have same correlation coefficient 0.63 with the target variable 'cnt'.
- From the above heatmap we can clearly see that the independent variables 'temp' and 'atemp' are highly correlated to the dependent variable 'cnt', followed by 'windspeed'.
- 'windspeed' and 'humidity' are correlated with a negative coefficient as humidity tends to be more when there is less wind.

Assumption - To get rid of independent variables with coefficient > 0.7 or < -0.7 with other independent variable(s).

![image](https://user-images.githubusercontent.com/103338455/162635514-0406c51a-4b9e-4d24-a252-14833c3dacf2.png)

Now that we have dropped 'atemp' , we don't have any other very highly correlated independent variables. We can now start with model building process.


# DATA PREPARATION

1. Creating Dummy variables for the categorical columns - 'weekday','mnth','season','weathersit','yr','holiday' & 'workingday'.
2. Splitting data into Train and Test in 70-30 proportion.
3. Rescaling the features of the training data using Min-Max Scaler.

![image](https://user-images.githubusercontent.com/103338455/162635649-f237d755-5a3d-47ef-a1a6-5eab137e7d80.png)

- The heatmap above displays the collinearity between independent variables and the dependent (cnt) variable.
- This also tells us about existing multi-collinearity between the independent variables.
- This will be helpful while considering multiple independent variables in model building step.

4. The hypothesis was be formulated as -

##### Null Hypothesis - H0 : Coefficients of the independent variables are insignificant
##### Alternate Hypothesis - H1 : Coefficients of the independent variables are significant


# MODEL BUILDING

1. Assumptions

- There is a linear relationship between X and y
- Error terms are normally distributed with a mean value 0
- Error terms have constant variance ( homoscedasticity )
- Error terms are independent of each other ( no multicollinearity )

Also we are going to assume 99% confidence interval. So, we will take into consideration p-value below 1% or p-value < 0.01. Similarly we will assume VIF limit of 5.

2. Splitting training data into X and y
3. RFE (Recursive Feature Elimination) - First we will use RFE for feature elimination. The columns we get from RFE will be considered for further manual refining of the model.
4. Building model using statsmodel, for the detailed statistics

Final model co-efficients and VIF:

![image](https://user-images.githubusercontent.com/103338455/162635862-a9805fba-525a-4752-ba93-784610880c71.png)

p-values for all variables are significant as they are exactly 0.

![image](https://user-images.githubusercontent.com/103338455/162635879-64f4c57c-3ab5-42ef-9dae-d68c745762c9.png)

VIF for all variables are < 5.


# MODEL EVALUATION

1. Residual Analysis on Training data

![image](https://user-images.githubusercontent.com/103338455/162635916-6e11c02d-8ff0-4e77-9162-fac61f74cccf.png)

Error terms are normally distributed with a mean value ~ 0.

![image](https://user-images.githubusercontent.com/103338455/162635931-df409fc3-bc27-4180-8ce3-faa064591958.png)

The above plot represents linear relationship between the dependent and independent variable.

![image](https://user-images.githubusercontent.com/103338455/162635988-42b2d780-74fc-4022-a6b9-0e56f0f7a7d7.png)

As we can see in the above plot, the variance of the residuals are almost constant. Hence, Homoscedasticity holds true by this model.

![image](https://user-images.githubusercontent.com/103338455/162636001-f17dbf56-8169-47f7-a3ed-07f6d290d31e.png)

None of the variables have coefficient > 0.7 or < -0.7. Hence, we can safely say that this model is free from multicollinearity.

2. Making Predictions Using the Final Model

![image](https://user-images.githubusercontent.com/103338455/162636036-d5600dbd-d823-4e45-9691-309a71c47a8f.png)

We can see that we have got a decent model here.

The equation for our model is -

##### cnt = 0.1264 + 0.5480 × temp + 0.2328 × yr_2019 + 0.1306 × season_Winter + 0.1011 × mnth_Sep + 0.0868 × season_Summer - 0.2838 × weathersit_Bad - 0.1533 × windspeed - 0.0992 × holiday_Yes - 0.0797 × weathersit_Fair

Since the coefficients of the independent variables are significant, we can reject the null hypothesis.

# CONCLUSION

The demand seems to be high on good weather days with high temperature. So, the company must take action to promote or give discounts during summer season and also ensure the availibilty of enough bikes to fulfill the high demand during summer months to increase their sales or in this case rental bike counts.
