# Top Bank Company - Churn Prediction

# 1.0 Context

# 2.0 Business Problem
    
TopBank is a large banking services company. It operates mainly in European countries offering financial products, from bank accounts to investments, as well as some types of insurance and investment products.
The business model of the company is service-oriented, i.e. it sells banking services to its customers through physical branches and an online portal.

The company's main product is a bank account, in which the client can deposit his salary, make withdrawals, deposits and transfer to other accounts. This bank account has no cost for the client and is valid for 12 months, that is, the client needs to renew the contract of this account to continue using for the next 12 months.

According to the TopBank Analytics team, each client who has this bank account returns a monetary value of 15% of their estimated salary. If the estimated salary is higher than the average, it returns 20% of that value during the current account period. This value is calculated annually.

For example, if a client's monthly salary is 1000 euros and the average of all bank salaries is 800 euros, the company therefore invoices 200 euros annually with this client. If this client is in the bank for 10 years, the company has already invoiced 2000 euros with its transactions and use of the account.

In recent months, the Analytics team has noticed that clients have been canceling their accounts and leaving the bank. This has reached unprecedented numbers in the company. Concerned with this rate increase, the team planned an action plan to decrease the rate of **evasion of clients**, also known as **Churn**.


> In general, Churn is a metric that indicates the **number of customers who have cancelled their contract or stopped purchasing their product** in a certain period of time. For example, customers who have cancelled their service contract or after its expiration have not renewed, are customers considered in churn.

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

#### Numerical Variables

![01](https://github.com/nickolasdias/topbankcompany/blob/master/image/01.png)

**Observations:**

#### Categorical Variables



### 3.1.2 Mental Hypothesis Map

![exited](https://github.com/nickolasdias/topbankcompany/blob/master/image/exited.jpg)

### 3.1.3 Exploratory Data Analysis

#### 3.1.3.1 Univariate Analysis - Target

![09](https://github.com/nickolasdias/topbankcompany/blob/master/image/09.png)

#### 3.1.3.2 Univariate Analysis - Numerical Variable

![10](https://github.com/nickolasdias/topbankcompany/blob/master/image/10.png)

**Observations:**

#### 3.1.3.3 Univariate Analysis - Categorical Variable

![11](https://github.com/nickolasdias/topbankcompany/blob/master/image/11.png)

**Observations:**

#### 3.1.3.4 Bivariate Analysis - Validation of the Hypothesis



#### 3.1.3.5 Multivariate Analysis - Numerical Variables - Pearson's Correlation

![29](https://github.com/nickolasdias/topbankcompany/blob/master/image/29.png)

**Observations:**

#### 3.1.3.6 Multivariate Analysis - Categorical Variables - Cramer V

![30](https://github.com/nickolasdias/topbankcompany/blob/master/image/30.png)

**Observations:**

#### 3.1.3.7 Multivariate Analysis - Numerical Variables and Binary Variables - Point Biserial Correlation

![31](https://github.com/nickolasdias/topbankcompany/blob/master/image/31.png)

**Observations:**

### 3.1.4 Machine Learning
