# Quantitative-Research-Virtual-Experience-Program-on-Forage
Quantitative Research (QR) is an expert quantitative modeling group at JPMorgan Chase, as well as a leader in financial engineering, data analytics, and portfolio management.

Reflections
Conducted comprehensive time series data analysis using Pandas to scrutinise historical natural gas prices. Successfully employed the Prophet model, achieving an RMSE less than 0.22 to project future prices.
Developed a prototype for natural gas storage contract pricing model in Python. This model leveraged Prophet’s forecast to automate contract quotations based on specified injection and withdrawal dates.
Examined loans data to assess the probability of customer default. Implemented and compared the performance of Logistic Regression, Random Forest, and XGBoost models. Notably, the XGBoost model outperformed others with an impressive accuracy score of 99.99%.
Devised methods to categorise FICO scores into buckets for enhanced defaults prediction. Utilised dynamic programming and a Genetic Algorithm, optimising for maximum log-likelihood, to transform these scores into categorical data.
Task 1 - Investigate and analyze price data
AIM:

pricing the natural gas storage contract Objectives:

OBJ1: extrapolate external data to increase granularity (Data preparation) OBJ2: analyse seasonality & annual trends OBJ3: price the contract using historical data to make future gas price prediction

Background info: Commodity storage contract: an agreement (between warehouse owners and participants in the supply chain) to store an agreed quality of any physical commodity in a warehouse for specified amount of time.

Key terms of such contracts:

periodic storage fees, withdraws/injections limits.
Injection date: is the time when the commodity is purchased and stored
Withdraw date: the commodity is withdrawn from the storage.
Data source: monthly snapshot of prices which represents the market price of natural gas delivered at the end of each calendar month. Data available for next 18mo + historical

Task: EDA historical data and an extrapolation for an extra year. Estimate purchase price at any date in the past and extrapolate for one year into the future.

Conclusions
Using Prophet function, the Mean Squred Errors is 0.218;
Mean Absolute Error is 0.376
Prophet can give a relative good prediction of this historical data
Task 2 - Create a prototype pricing model
Aim:

Write a function that is able to use the data you created previously to price the contract.

You can assume there is no transport delay and that interest rates are zero. Market holidays, weekends, and bank holidays need not be accounted for. Test your code by selecting a few sample inputs.

Model input:

Injection dates.
Withdrawal dates.
The prices at which the commodity can be purchased/sold on those dates.
The rate at which the gas can be injected/withdrawn.
The maximum volume that can be stored.
Storage costs.
Model output: estimated price model

Price_sell/ _buy = Price * Volume
Price_contract = Price_sell - Price_buy - cost
cost = Gas_Inj_Withdraw + Storage + Transport
Transport = Transport_per_time *2
Storage = Storage_rate * Storage_time
Storage_time = Withdraw_date - In_date
Task 3 - Predict the PD (Probability of default) for a borrower
Aim Use the provided data to train a function that will estimate the probability of default for a borrower.

Objectives

Produce a function that can take in the properties of a loan and output the expected loss.
Explore some technique including
Simple regression: -- Accuracy of the Logistic Regression model is: 0.99; Accuracy of Logisitic Regression model after replace variable is: 0.9979
XGBoost: -- Accuracy of the XGBoost is 0.9998
Random forest: -- Accuracy of the Random Forest model is 0.9997
Raw data info:

borrower
income
total loans outstanding
Previsouly defaulted on a loan
Assuming a recovery rate of 10%, this can be used to give the expected loss on a loan.
Conclusions
Simple regression: -- Accuracy of the Logistic Regression model is: 0.99; Accuracy of Logisitic Regression model after replace variable is: 0.9979
XGBoost: -- Accuracy of the XGBoost is 0.9998
Random forest: -- Accuracy of the Random Forest model is 0.9997
Task 4: Bucket FICO scores
Charlie wants to build a machine learning model that will predict the probability of default, but while you are discussing the methodology, she mentions that the architecture she is using requires *categorical data*. As FICO ratings can take integer values in a large range, they will need to be mapped into *buckets*.

Defination

FICO (Fair Isaac Corportation)

Founders: Bill Fair/ Earl Isaac

A FICO score is a standardized credit score created by the Fair Isaac Corporation (FICO) that quantifies the creditworthiness of a borrower to a value between 300 to 850, based on various factors.

FICO scores are used in 90% of mortgage application decisions in the United States.

Task

The risk manager provides you with FICO scores for the borrowers in the bank’s portfolio and wants you to construct a technique for predicting the PD (probability of default) for the borrowers using these scores.

Aim
Create a rating map that maps the FICO score of the borrowers to a rating where a lower rating signifies a better credit score.
You could consider many ways of solving the problem by optimizing different properties of the resulting buckets, such as the mean squared error or log-likelihood
Conclusions
Method 1: Using Dynamic Programming
log likelyhood: -4217.8245
results: [850, 753, 752, 732, 696, 649, 611, 580, 552, 520, 300]
Method 2: Using genetic algorithm to optimise
log likelyhood: -4243.0575
results: [850, 765, 729, 715, 696, 637, 608, 552, 541, 510, 300]
