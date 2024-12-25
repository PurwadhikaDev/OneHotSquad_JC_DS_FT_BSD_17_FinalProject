**Business Problem Understanding**

A marketing campaign is a set of commercial operations all pursuing the same objective, which may concern the improvement of brand awareness and/or sales objectives. If in the past the majority of commercial operations were based on mass marketing, nowadays direct or even targeted marketing is more and more desired. Companies use direct marketing strategies when they target customer segments by contacting them to achieve a specific sales campaign.

Direct marketing ultimately aims to establish cost-effective, two-way and one-to-one communications with individual customers, which is not restricted to the internet; most direct marketing communication is still performed via traditional channels, such as direct mail, sms, email and inbound and outbound calls. To achieve efficient direct marketing, possessing information about the present and estimating future customer preferences is a fundamental requirement. In the current business climate, customer preferences change dynamically, and they are too complicated to derive direct conclusions.

Direct marketing campaigns are essential instruments for enhancing the economic gain of a firm in two respects: obtaining new customers and creating additional yield from present customers.

In this dataset we have data that describing Portugal bank marketing campaigns results. Conducted campaigns were based mostly on direct phone calls, offering bank client to place a term deposit. If after all marketing efforts client had agreed to place deposit - target variable marked 'yes', otherwise 'no'.

**Data Understanding**

Our Data is imbalance, have "unknown as missing value", and have outlier.

**Machine Learning**

XGboost is the best model using RandomUnderSampler as resampling with F2 score 0.524

**Conclusion**
*   The metric that we used is F2 score because we make a Recall value more important than a Precision one. In other words, it focuses on minimizing False Negatives than minimizing False Positives. The best F2 score is 0.532.

*   If we call all of our customer without machine learning, assume that we contact 8016 customer (20% from our data) and we just have 2 results, False Positive and True Positive. So, the total error cost that we lost if we call all the customer:  
    *   False Positive = 7110 customers (88,8% from data test)
    *   True Positive = 906 customers (11,2% from data test)
    *   Total cost due to false positive (customer that we call but didn't subscribe) => 7110 x 500 EURO = 3555000 EURO
    *   Total Customer that have potentian to subcribe but didn't subscribe => 0 customer (because we call all of the customer)

So, if we don't use machine learning and we call all of our customers, the total error cost is 3555000 EURO

*   If we use machine learning, we know how many customer that is predicted subscribe and actually not subscribe (False Positif) and customer who are predicted not subscribe and actually subscribe (False Negative). So, the total cost from our error:
    *   False Positive = 1065 customers 
    *   False Negative = 309 customers
    *   Error cost => (1065 x 500) + (309 x 2000) = 1151500 EURO

*   So, we can reduce the error cost: 
    *   Reduce error cost => 3555000 EURO (without machine learning) - 1151500 EURO (with machine learning) = 2403500 EURO or around 67.6%

**Recommendation**
*   All the processes in here including business understanding, data cleaning, EDA, ML modeling, hyperparam tuning etc. already followed common practice in ML implementation.
Unfortunately, the score result is not considered good. Therefore, if there are more data in the future we hope that the score will also be improved.
*   Our data is highly imbalance, so it is better to gather more data to reduce the imbalace data.
*   Add more features that likely have correlation to the target to improve the metrics score.
*   Try to use another machine learning algorithm and hyperparameter tuning again.
