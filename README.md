# INTRODUCTION

This case study aims to give an idea of applying linear regression in a real business scenario for a bike-sharing provider "BoomBikes" to model the demand for shared bikes with the available independent variables. It will be used by the management to understand how exactly the demands vary with different features. They can accordingly manipulate the business strategy to meet the demand levels and meet the customer's expectations. Further, the model will be a good way for management to understand the demand dynamics of a new market. 

# DATA EXPLORATION AND CLEANING

- In the data set we had few columns which did not contribute towards business goal and thus could be ignored for our analysis. Such columns were instant, dteday, casual and registered. We have dropped these columns.
- There were few categorical columns in this data set which hold the values in numerical form. Those were converted to their respective categorical form as per the data dictionary for better representation and understanding of data. 
- It was assumed that 0 - 6 represent Sunday - Saturday.

# EDA AND DATA VISUALIZATION

In this step we visualized and explored the categorical as well as continuous variables present in the data set.
From the data set we could see that the columns 'temp','atemp','hum','windspeed' and 'cnt' are numerical in nature. We plotted distribution plot for them to understand better.

![image](https://user-images.githubusercontent.com/103338455/162635165-22dd4e82-6ac2-481c-bc56-32d5cf46809b.png)



# DATA PREPARATION

# MODEL BUILDING

# MODEL EVALUATION

# CONCLUSION

The demand seems to be high on good weather days with high temperature. So, the company must take action to promote or give discounts during summer season and also ensure the availibilty of enough bikes to fulfill the high demand during summer months to increase their sales or in this case rental bike counts.
