# Top Bank Company - Churn Prediction

# 1.0 Context

In general, Churn is a metric that indicates the **number of customers who have cancelled their contract or stopped purchasing their product** in a certain period of time. For example, customers who have cancelled their service contract or after its expiration have not renewed, are customers considered in churn.

# 2.0 Business Problem
    
Top Bank is a large banking services company. It operates mainly in European countries offering financial products, from bank accounts to investments, as well as some types of insurance and investment products.
The business model of the company is service-oriented, i.e. it sells banking services to its customers through physical branches and an online portal.

The company's main product is a bank account, in which the client can deposit his salary, make withdrawals, deposits and transfer to other accounts. This bank account has no cost for the client and is valid for 12 months, that is, the client needs to renew the contract of this account to continue using for the next 12 months.

According to the TopBank Analytics team, each client who has this bank account returns a monetary value of 15% of their estimated salary. If the estimated salary is higher than the average, it returns 20% of that value during the current account period. This value is calculated annually.

For example, if a client's monthly salary is 1000 euros and the average of all bank salaries is 800 euros, the company therefore invoices 200 euros annually with this client. If this client is in the bank for 10 years, the company has already invoiced 2000 euros with its transactions and use of the account.

In recent months, the Analytics team has noticed that clients have been canceling their accounts and leaving the bank. This has reached unprecedented numbers in the company. Concerned with this rate increase, the team planned an action plan to decrease the rate of **evasion of clients**, also known as **Churn**.


<h2> The Challange </h2>

TopBank requested an action plan to decrease the number of customers by **churn** and show the financial return of the solution.

At the end of the consultancy, a production model will have to be delivered to TopBottom's CEO, who will receive a client base via API and develop this "scored" base, i.e. an extra column with the probability of each client going into churn. In addition, you will also need to deliver a report reporting on the model's performance and results, answering future questions

- What is the company's current Churn rate?

- How the Churn rate varies monthly ?

- What is the performance of the model in classifying customers in Churn?

- What is the expected return, in terms of invoicing, if the company uses the model to avoid the Churn of the clients?


<h2> Presenting the Data </h2>

The data are available in this [link](https://www.kaggle.com/mervetorkan/churndataset).

<h2> Objectives </h2>

- **Create an action plan**.

- **Place the model in production**.

- **Submit a report reporting the results**.

- **Answer the questions**.

# 3.0 Solution

In this project, we developed a model that classifies customers in churn ot not.

## 3.1 Main Steps

### 3.1.1 Data Describe - Statistics Descriptive

#### 3.1.1.1 Numerical Variables

![01](https://github.com/nickolasdias/topbankcompany/blob/master/image/01.png)

**Relavants Observations:**

- The average credit for consumption is 650,75 euros.
- The average age of the bank's clients is 38.94 years.
- The average number of months that customers remained active is 5 months.
- The average balance of the customers' account is 76.381,21 euros.
- The average number of products purchased by the bank's clients is 1.53.
- The minimum estimated salary of some people is 11.58 euros. This result is suspect compared to the average estimated salary of 99.730,08 euros.

#### 3.1.1.2 Checking Outliers

![02](https://github.com/nickolasdias/topbankcompany/blob/master/image/02.png)

**Observation:**

- We can observe that the ages are characterized as outliers over 62.

![03](https://github.com/nickolasdias/topbankcompany/blob/master/image/03.png)

**Observation:**

- We can observe that the credit score is characterized with outliers below 384.5.

![04](https://github.com/nickolasdias/topbankcompany/blob/master/image/04.png)

**Observation:**

- We can observe that there are no outliers.

![05](https://github.com/nickolasdias/topbankcompany/blob/master/image/05.png)

**Observation:**

- We can observe that there are no outliers, but there are many null balance values in the first quartile.

![06](https://github.com/nickolasdias/topbankcompany/blob/master/image/06.png)

**Observation:**

- We can observe that there are no outliers.

#### 3.1.1.3 Categorical Variables

![07](https://github.com/nickolasdias/topbankcompany/blob/master/image/07.png)

**Observations:**

- The estimated salary of the male gender is higher than the estimated salary of the female gender. And the French have the highest estimated salaries.
- The balance of the male gender is highter than the balance of the female gender.
- The male gender has more banking products than the female gender. And the French the largest purchases of banking products.

![08](https://github.com/nickolasdias/topbankcompany/blob/master/image/08.png)

**Observations:**

- Credit Card x Balance: There is no difference in the balance of credit card customers compared to non-credit card customers.
- Credit Card x Estimated Salary: There is no difference in the estimated salaries of customers with or without credit cards.
- Credit Card x Number of Products: There is no difference in the number of products with customers who have a credit card or not.
- Active Member x Balance: Customers with bank transactions and without bank transactions have practically the same median between their balances.
- Active Member x Estimated Salary: There is no difference in the estimated salaries of customers with banking transactions or not.
- Active Member x Number of Products: There is no difference in the number of products with customers who have banking transactions or not.

### 3.1.2 Mental Hypothesis Map

![exited](https://github.com/nickolasdias/topbankcompany/blob/master/image/exited.jpg)

#### 3.1.2.1 Creating Hypotheses

**H1.** Male customers have more risk of exit than female customers.

**H2.** German customers have a high risk of exit more than  Spanish and French customers.

**H3.** Old customers run a higher risk of exit than young customers.

**H4.** Customers who remained active for more than 5 months have a low risk of exit than customers who remained active for less than 5 months.

**H5.** Customers with monetary values above 100.000 euros have a low risk of exit than customers with monetary values below 100.000 euros.

**H6.** Customers that have estimated salaries above 100.000 euros have a low risk of exit than customers that have estimated salaries below 100.000 euros.

**H7.** Customers that have more than 2 banking products have a low risk of exit than customers that have less than 2 banking products.

**H8.** Customers with a credit card have a low risk of exit than customers without a credit card.

**H9.** Customers with bank transactions have a low risk of exit than customers without bank transactions.

**H10.** Customers with credit above 650 euros have a low risk of exit than customers with credit below 650 euros.

**H11.** Customers with credit cards and bank transactions have a low risk of leaving the bank.

**H12.** Customers who have remained active and with a credit card have a low risk of leaving the bank.

**H13.** Customers who have remained active and with bank movements have low risk of leaving the bank.

**H14.** Customers with low salaries are more likely to leave the bank than customers with medium and high salaries.

### 3.1.3 Exploratory Data Analysis

#### 3.1.3.1 Univariate Analysis - Target

![09](https://github.com/nickolasdias/topbankcompany/blob/master/image/09.png)

**Observations:**

Exited Customers:

- yes: 20.47%
- no : 79.53%

#### 3.1.3.2 Univariate Analysis - Numerical Variable

![10](https://github.com/nickolasdias/topbankcompany/blob/master/image/10.png)

**Observations:**

- The credit score is close to a normal distribution.
- Most customers are between 30 and 40 years of age.
- There is a balance between the number of months customers have been active at the bank.
- More than 2500 customers (+ 32.41%) have a zero account value.
- More than 95% of customers have between 1 and 2 products.
- There is a balance between the number of customers and their estimated salaries.

#### 3.1.3.3 Univariate Analysis - Categorical Variable

![11](https://github.com/nickolasdias/topbankcompany/blob/master/image/11.png)

**Observations:**

- There are more French customers (49.90%) than German (25.02%) and Spanish (25.08%) customers in the bank.
- There are more male customers (54.87%) than female customers (45.13%) in the bank.
- There are more customers with credit cards (70.99%) than customers without credit cards (29.01%) in the bank.
- There is a balance between customers having bank transactions with customers (51.36%) who do not have bank transactions (48.64%).
- There are more adult customers (94.70%) than young and old customers (0.04% and 4.86%) in the bank.
- About 87.70% of clients have high estimated salaries, 8.71% have medium estimated salaries and 3.59% have low estimated salaries.
- 4709 customers have balance and remained active in the bank. And 3005 customers only remained active, but without balance.
- 2535 customers have a balance and have made bank movements. 2394 customers only have a balance and have not made bank transactions. 1427 customers only made bank movements. And 1358 customers made nothing.
- There are more customers who have a credit card and have made bank transactions (36.36%) and also more customers who only have a credit card (34.63%).
- There are more customers that have remained active and have credit cards (68.32%).
- There is a balance between the number of customers who remained active with banking transactions than customers who only remained active (49.16% and 46.64%).


#### 3.1.3.4 Bivariate Analysis - Some Validations of Hypothesis

**H1. Male customers have more risk of leaving the bank than female customers. (FALSE)**

![12](https://github.com/nickolasdias/topbankcompany/blob/master/image/12.png)

**Observations:**

- Female customers have a higher risk of exit than male customers.

**H3. Old customers have a higher risk of leaving the bank than young customers. (FALSE)**

![14](https://github.com/nickolasdias/topbankcompany/blob/master/image/14.png)

**Observation:**

- Adult customers have a high risk of leaving the bank than old or young customers.

**H5. Customers with monetary values above 100.000 euros have a low risk of leaving the bank than customers with monetary values below 100.000 euros. (FALSE)**

**Monetary Values below 100.000 euros**

![16](https://github.com/nickolasdias/topbankcompany/blob/master/image/16.png)

**Observation:**

- About 16% of clients with below average monetary values exited the bank.

**Monetary Values above 100.000 euros**

![17](https://github.com/nickolasdias/topbankcompany/blob/master/image/17.png)

**Observation:**

- About 25% of customers with above average monetary values left the bank.

**H7. Customers who have more than 2 banking products have a low risk of leaving the bank than customers that who less than 2 banking products.(TRUE)**

![20](https://github.com/nickolasdias/topbankcompany/blob/master/image/20.png)

**Observation:**

- Customers who have more than 2 banking products have a low exit risk than customers who have less than 2 banking products.

**H10. Customers with credit above 650 euros have a low risk of leaving the bank than customers with credit below 650 euros. (TRUE)**

**Credit Score below 650 euros**

![23](https://github.com/nickolasdias/topbankcompany/blob/master/image/23.png)

**Observation:**

- About 21.68% of customers with below average credit left the bank.

**Credit Score above 650 euros**

![24](https://github.com/nickolasdias/topbankcompany/blob/master/image/24.png)

**Observation:**

- About 19.30% of customers with above average credit left the bank.

**H11. Customers with credit cards and bank transactions have a low risk of leaving the bank. (FALSE)**

![25](https://github.com/nickolasdias/topbankcompany/blob/master/image/25.png)

**Observation:**

- Customers with only bank transactions have a low risk of leaving the bank than other customers.

**H14. Customers with low salaries are more likely to leave the bank than customers with medium and high salaries. (FALSE)**

![28](https://github.com/nickolasdias/topbankcompany/blob/master/image/28.png)

**Observations:**

- Customers with high salaries (87.14%) are more likely to leave the bank than customers with low and medium salaries (3.55% and 9.31%).

#### 3.1.3.5 Multivariate Analysis - Numerical Variables - Pearson's Correlation

![29](https://github.com/nickolasdias/topbankcompany/blob/master/image/29.png)

**Relevant Correlations:**

- `balance` and `num_of_products`: **-0.31**.

#### 3.1.3.6 Multivariate Analysis - Categorical Variables - Cramer V

![30](https://github.com/nickolasdias/topbankcompany/blob/master/image/30.png)

**Relevant Correlations:**

 - `geography` and `balance`: **0.41**
 
 - `geography` and `balance_active`: **0.31**
 
 - `has_cr_card` and `has_cr_card_active_member`: **1**
 
 - `has_cr_card` and `tenure_has_cr_card`: **0.98**
 
 - `is_active_member` and `balance_active`: **1**
 
 - `is_active_member` and `has_cr_card_active_member`: **1**
 
 - `is_active_member` and `tenure_is_active_member`: **0.98**
 
 - `balance_tenure` and `balance_active`: **0.94**
 
 - `balance_active` and `has_cr_card_active_member`: **0.58**
 
 - `balance_active` and `tenure_is_active_member` : **0.69**
 
 - `has_cr_card_active_member` and `tenure_has_cr_card`: **0.69**
 
 - `has_cr_card_active_member` and `tenure_is_active_member`: **0.69**
 
 - `tenure_has_cr_card` and `tenure_is_active_member` : **0.71**

#### 3.1.3.7 Multivariate Analysis - Numerical Variables and Binary Variables - Point Biserial Correlation

![31](https://github.com/nickolasdias/topbankcompany/blob/master/image/31.png)

**Relevant correlations:**

- `age`and `exited`: **0.30**
- `balance`and `exited`: **0.12**

### 3.1.4 Machine Learning Modeling

* Logistic Regression
* Random Forest Classifer
* Catboost Classifier
* LGBM Classifier
* KNeighbors Classifier

#### 3.1.4.1 Logistic Regression

![32](https://github.com/nickolasdias/topbankcompany/blob/master/image/32.png)

**Observations:**

- actual not churn x predict not churn: 5933
- actual not churn x predict churn: 202
- actual churn x predict not churn: 1320
- actual churn x predict churn: 259

#### 3.1.4.2 Random Forest Classifier

![33](https://github.com/nickolasdias/topbankcompany/blob/master/image/33.png)

**Observations:**

- actual not churn x predict not churn: 5936
- actual not churn x predict churn: 199
- actual churn x predict not churn: 877
- actual churn x predict churn: 702

#### 3.1.4.3 Catboost Classifier

![34](https://github.com/nickolasdias/topbankcompany/blob/master/image/34.png)

**Observations:**

- actual not churn x predict not churn: 5895
- actual not churn x predict churn: 240
- actual churn x predict not churn: 824
- actual churn x predict churn: 755

#### 3.1.4.4 LGBM Classifier

![35](https://github.com/nickolasdias/topbankcompany/blob/master/image/35.png)

**Observations:**

- actual not churn x predict not churn: 5883
- actual not churn x predict churn: 252
- actual churn x predict not churn: 799
- actual churn x predict churn: 780

#### 3.1.4.5 KNN Classifier

![36](https://github.com/nickolasdias/topbankcompany/blob/master/image/36.png)

**Observations:**

- actual not churn x predict not churn: 5813
- actual not churn x predict churn: 322
- actual churn x predict not churn: 1058
- actual churn x predict churn: 521

#### 3.1.4.6 Performance Comparison

![37](https://github.com/nickolasdias/topbankcompany/blob/master/image/37.png)

**Observations:**

- Based on the Business context and in order to better accomplish the project goals, deliverables and deployment, the chosen model is **Random Forest Classifier**.

### 3.1.5 Hyperparameter Fine Tuning

In this project to fine tune the hyperparameters of the classifier, we use the best parameters determined by `RandomizedSearch()`.

Therefore, we apply the base model and the fitted model in the test data to check their performances.

#### 3.1.5.1 Tuned Model x Base Model Performance Comparison on Test Set

**Base Model Performance**

![44](https://github.com/nickolasdias/topbankcompany/blob/master/image/44.png)

![38](https://github.com/nickolasdias/topbankcompany/blob/master/image/38.png)

**Observations:**

- actual not churn x predict not churn: 1481
- actual not churn x predict churn: 112
- actual churn x predict not churn: 196
- actual churn x predict churn: 211

**Tuned Model Performance**

![45](https://github.com/nickolasdias/topbankcompany/blob/master/image/45.png)

![39](https://github.com/nickolasdias/topbankcompany/blob/master/image/39.png)

**Observations:**

- actual not churn x predict not churn: 1477
- actual not churn x predict churn: 116
- actual churn x predict not churn: 197
- actual churn x predict churn: 210

Analyzing the two models applied in the test data set, the **base model** has a better performance than the tuned model.

### 3.1.6 Model and Business Performance

#### 3.1.6.1 Model Performance

**Precision and Recall versus Threshold**

![40](https://github.com/nickolasdias/topbankcompany/blob/master/image/40.png)

**Observations:**

- The threshold between precision and recall is 51%.

**Precision versus Recall**

![41](https://github.com/nickolasdias/topbankcompany/blob/master/image/41.png)

**Cumulative Gains Curve**

![42](https://github.com/nickolasdias/topbankcompany/blob/master/image/42.png)

**Lift Curve**

![43](https://github.com/nickolasdias/topbankcompany/blob/master/image/43.png)

#### 3.1.6.2 Business Performance 

**Performance of the model and results report:**


 * What is the company's current churn rate ? The company's current **churn rate is 20.35%.**
 
 
 * How the churn rate varies per month ? It is not possible to determine the churn variation per month, as the available data does not have information per month. What can be calculated is the churn variation per tenure (number of years that the customer was active).
 
 
 * What is the performance of the model to label customers as churns? The model has a **precision** of **65.32%**.And it detects about **51.84%** of the clients that are in churn.
 
 
 * What is the revenue of the company, if the company avoids that the clients enter in churn through the developed model? The revenue of the company is around 38.079.850,98 euros, considering that no client enters in churn. And the revenue lost by the company if all the 407 clients go into churn is 7.491.850,97 euros.
 
**Scenario according the model:**

 * Company's revenue if 211 clients don't get into churn through the model: 4.106.314,45
 * That represents 51.84% of clients labeled in churn and 54.81% of the total revenue loss.
 
**Possible measure: discount coupon or other financial incentive.**
 * Which customers could receive an incentive and at what cost, in order to maximize the ROI (Return on investment)? (The sum of incentives shall not exceed 10.000 euros). 
 
The best solution to know which customers could receive the financial incentive to maximize ROI is alternative 03, because the value of the incentive is given according to the probability of expected turnover of the model using the Backpack Problem.

Therefore, we will have the following results:

 * Recovered Revenue: 3,668,096.16
 * % Recovered from Total Revenue loss: 48.96%
 * Investiment: 10.000,00
 * Profit: 3.658.096,16
 * ROI: 36.580,96
 * Potencial clients recovered acc. model: 137
 * Potencial churn reduction: 33.66%

# References
