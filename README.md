# Elo-Merchant-Category-Recommendation
This is a Kaggle project which can be found at:https://www.kaggle.com/c/elo-merchant-category-recommendation/. The comepetition somehow can't be accessed for now.

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

![](.\img\RMSE.png)
