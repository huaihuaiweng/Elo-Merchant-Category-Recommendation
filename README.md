# Elo-Merchant-Category-Recommendation
This is a Kaggle project which can be found at: [here](ttps://www.kaggle.com/c/elo-merchant-category-recommendation/.) However, somehow the comepetition currently can't be accessed.

Elo is one of the largest payment brands in Brazil. It has built partnerships with merchants to offer promotions or discounts to their card holders. However, questions like whether these promotions are suitable for the customers and the merchants; whether the customers like this consumption experience and whether customers have increased for the merchants are raised. Therefore, personalization is the key for answering the questions.

As a result, Elo has built a machine learning model trying to analyze customers’ most significant factors affecting their preference. However, until now, they are still not able to provide customized experience for their customers. In the competition, we need to develop an algorithm to measure a customer’s loyalty based on his/her consumption history to improve their consumption experience and also help Elo reduce unnecessary commercial events.

# Data description
There are five files in total provided. All data is simulated and fictitious, and is not real customer data. The reference date is set to be 2018/2/1
1. train.csv: the training set
2. test.csv: the testing set
3. historical_transactions.csv: transactions records that are made 2 month to 5 month ago from the reference date.
4. merchants.csv: additional information about all merchants. We did not use the information in this file.
5. new_merchants_transactions.csv: transactions records that are made within 2 months from the reference date.

# Evaluation metric
Root Mean Squared Error(RMSE)
Submissions are scored on the root mean squared error.
RMSE is defined as: 
<p align="center">
    <img src="/img/RMSE.png" width="20%"/>
<p>

, where y_i is the actual loyalty score assigned to each card_id and y^_i is the predicted loyalty score.

# Data understanding
## Data description
### 1.1 train.csv
| Columns            | Description                                                              | Type      | Range                                                               |
|--------------------|--------------------------------------------------------------------------|-----------|---------------------------------------------------------------------|
| card_id            | Unique card identifier (e.g. C_ID_4e6213e9bc)                            | Category  |                                                                     |
| first_active_month | Month of first purchase, YYYY-MM                                         | Category  | 2011-11 ~ 2018-02                                                   |
| feature_1          | Anonymized card categorical feature                                      | Numerical | {1,2,3,4,5}                                                         |
| feature_2          | Anonymized card categorical feature                                      | Numerical | {1,2,3}                                                             |
| feature_3          | Anonymized card categorical feature                                      | Numerical | {0,1}                                                               |
| target             | Loyalty score calculated 2 months after historical and evaluation period | Numerical | min: -33.219281 </br> max: 17.9650684</br> mean: 3.850500</br> std: -0.393636 |

### 1.2 historical_transaction.csv
up to 2 months' worth of historical transactions for each card_id
| Columns              | Description                                                            | Type        | Range                                                                                   |
|----------------------|------------------------------------------------------------------------|-------------|-----------------------------------------------------------------------------------------|
| card_id              | Unique card identifier (e.g. C_ID_4e6213e9bc)                          | Categorical |                                                                                         |
| month_lag            | month lag to reference date                                            | Numerical   | {-13,-12,...,-1,0}                                                                      |
| authorized_flag      | {'Y' if approved; 'N' if denied}                                       | Categorical | {N,Y}                                                                                   |
| category_1           | Anonymized category                                                    | Categorical | {N,Y}                                                                                   |
| category_2           | Anonymized category                                                    | Numerical   | {1,2,3,4,5}                                                                             |
| category_3           | Anonymized category                                                    | Categorical | {A,B,C}                                                                                 |
| city_id              | City identifier (anonymized)                                           | Numerical   | {-1,1,2,...,347}                                                                        |
| installments         | Number of installments of purchase                                     | Numerical   | {-1,0,1,...,12,999}                                                                     |
| merchant_id          | Merchant identifier (anonymized) (e.g. M_ID_e020e9b302)           | Categorical |                                                                                         |
| merchant_category_id | Merchant category identifier (anonymized)                              | Numerical   | {-1,1,2,...,891}                                                                        |
| purchase_amount      | Normalized purchased amount                                            | Numerical   | min: -7.469078e-01</br> max: 6.010604e+06</br> mean: 3.64009e-02</br> std: 1.123522e+03 |
| purchase_date        | Purchase date </br> YYYY-MM-DD hh:mm:ss </br> (ex:2017-06-25 15:33:07) | date        |                                                                                         |
| state_id             | State identifier (anonymized)                                          | hh:mm:ss    | {-1,1,2,...24}                                                                          |
| subsector_id         | Merchant category group identifier (anonymized)                        | 15:33:07)   | {-1,1,2,...24}                                                                          |

### 1.3 new_merchant_transaction.csv
Two months' worth of data for each card_id containing ALL purchases that card_id made at merchant_ids that were not visited in the historical data. The only difference between new_merchant_transaction and historical_transactions is that the values for “month_lag” in new_merchant_transanction is {1,2}. Size : ( 1963031,14 )

# EDA
[The notebook displaying EDA steps and results](https://github.com/huaihuaiweng/Elo-Merchant-Category-Recommendation/blob/main/Elo_project_EDA.ipynb)
# Feature engineering and modeling
[The notebook displaying feature engineering and model steps and results](https://github.com/huaihuaiweng/Elo-Merchant-Category-Recommendation/blob/main/Elo_project_modeling.ipynb)
# Result
Our public score on kaggle is 3.9305, which ranks no.1450 on the leaderboard (surpassed 66% of the competitors). The private score is 3.61646, ranking no.1097 on the leaderboard(surpassed 75% of the competitors).

|                   |  Public score  |  Private score |
|:-----------------:|:--------------:|:--------------:|
| sample submission | 3.95214(3.41%) | 3.87852(1.02%) |
|     our model     |  3.69305(66%)  |  3.61646(75%)  |
