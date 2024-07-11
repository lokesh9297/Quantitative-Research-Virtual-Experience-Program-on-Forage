# Quantitative Research Virtual Experience Program on Forage

Quantitative Research (QR) is an expert quantitative modeling group at JPMorgan Chase, as well as a leader in financial engineering, data analytics, and portfolio management.

## Reflections

### Time Series Data Analysis

- Conducted comprehensive time series data analysis using Pandas to scrutinize historical natural gas prices.
- Successfully employed the Prophet model, achieving an RMSE less than 0.22 to project future prices.

### Natural Gas Storage Contract Pricing Model

- Developed a prototype for a natural gas storage contract pricing model in Python.
- Leveraged Prophet’s forecast to automate contract quotations based on specified injection and withdrawal dates.

### Loan Default Probability Assessment

- Examined loans data to assess the probability of customer default.
- Implemented and compared the performance of Logistic Regression, Random Forest, and XGBoost models.
- Notably, the XGBoost model outperformed others with an impressive accuracy score of 99.99%.

### FICO Score Categorization for Enhanced Defaults Prediction

- Devised methods to categorize FICO scores into buckets for enhanced defaults prediction.
- Utilized dynamic programming and a Genetic Algorithm, optimizing for maximum log-likelihood, to transform these scores into categorical data.

## Task 1 - Investigate and Analyze Price Data

**Aim:**

Pricing the natural gas storage contract.

**Objectives:**

- **OBJ1:** Extrapolate external data to increase granularity (Data preparation)
- **OBJ2:** Analyze seasonality & annual trends
- **OBJ3:** Price the contract using historical data to make future gas price prediction

**Background Info:**

Commodity storage contract: an agreement (between warehouse owners and participants in the supply chain) to store an agreed quality of any physical commodity in a warehouse for a specified amount of time.

**Key Terms:**

- **Periodic Storage Fees:** Withdraws/injections limits.
- **Injection Date:** The time when the commodity is purchased and stored.
- **Withdraw Date:** The commodity is withdrawn from the storage.

**Data Source:**

Monthly snapshot of prices which represents the market price of natural gas delivered at the end of each calendar month. Data available for next 18 months + historical.

**Task:** EDA historical data and extrapolation for an extra year. Estimate purchase price at any date in the past and extrapolate for one year into the future.

**Conclusions:**

- Using Prophet function, the Mean Squared Error is 0.218
- Mean Absolute Error is 0.376
- Prophet can give a relatively good prediction of this historical data.

## Task 2 - Create a Prototype Pricing Model

**Aim:**

Write a function that is able to use the data you created previously to price the contract.

**Model Input:**

- Injection dates
- Withdrawal dates
- The prices at which the commodity can be purchased/sold on those dates
- The rate at which the gas can be injected/withdrawn
- The maximum volume that can be stored
- Storage costs

**Model Output:**

- Estimated price model
- Price_sell/ _buy = Price * Volume
- Price_contract = Price_sell - Price_buy - cost
- cost = Gas_Inj_Withdraw + Storage + Transport
- Transport = Transport_per_time * 2
- Storage = Storage_rate * Storage_time
- Storage_time = Withdraw_date - Injection_date

## Task 3 - Predict the PD (Probability of Default) for a Borrower

**Aim:** Use the provided data to train a function that will estimate the probability of default for a borrower.

**Objectives:**

Produce a function that can take in the properties of a loan and output the expected loss.

**Techniques Explored:**

- Simple regression
  - Accuracy of the Logistic Regression model is: 0.99
  - Accuracy of Logistic Regression model after replacing variable is: 0.9979
- XGBoost
  - Accuracy of the XGBoost is 0.9998
- Random forest
  - Accuracy of the Random Forest model is 0.9997

**Raw Data Info:**

- Borrower
- Income
- Total loans outstanding
- Previously defaulted on a loan

Assuming a recovery rate of 10%, this can be used to give the expected loss on a loan.

**Conclusions:**

- Simple regression
  - Accuracy of the Logistic Regression model is: 0.99
  - Accuracy of Logistic Regression model after replacing variable is: 0.9979
- XGBoost
  - Accuracy of the XGBoost is 0.9998
- Random forest
  - Accuracy of the Random Forest model is 0.9997

## Task 4 - Bucket FICO Scores

**Definition:**

FICO (Fair Isaac Corporation)

- Founders: Bill Fair / Earl Isaac
- A FICO score is a standardized credit score created by the Fair Isaac Corporation (FICO) that quantifies the creditworthiness of a borrower to a value between 300 to 850, based on various factors.
- FICO scores are used in 90% of mortgage application decisions in the United States.

**Task:**

The risk manager provides you with FICO scores for the borrowers in the bank’s portfolio and wants you to construct a technique for predicting the PD (probability of default) for the borrowers using these scores.

**Aim:**

Create a rating map that maps the FICO score of the borrowers to a rating where a lower rating signifies a better credit score.

You could consider many ways of solving the problem by optimizing different properties of the resulting buckets, such as the mean squared error or log-likelihood.

**Conclusions:**

- **Method 1:** Using Dynamic Programming
  - Log-likelihood: -4217.8245
  - Results: [850, 753, 752, 732, 696, 649, 611, 580, 552, 520, 300]
- **Method 2:** Using Genetic Algorithm to Optimize
  - Log-likelihood: -4243.0575
  - Results: [850, 765, 729, 715, 696, 637, 608, 552, 541, 510, 300]
