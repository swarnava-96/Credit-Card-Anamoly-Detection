# Credit-Card-Anamoly-Detection

#### Goal: In this project, I have applied Unsupervised Learning algorithms to detect whether a credit card transaction is Fraudulent or not. 
Isolation Forest, Local Outlier Factor and One Class SVM will be used and compared.

## About the Data set:
The data set was downloaded from [Kaggle](https://www.kaggle.com/mlg-ulb/creditcardfraud/version/3). 

It is important that credit card companies are able to recognize fraudulent credit card transactions so that customers are not charged for items that they did not purchase.

The dataset contains transactions made by credit cards in September 2013 by European cardholders.
This dataset presents transactions that occurred in two days, where we have 492 frauds out of 284,807 transactions.
The dataset is highly unbalanced, the positive class (frauds) account for 0.172% of all transactions.

It contains only numerical input variables which are the result of a PCA transformation. 
Unfortunately, due to confidentiality issues, the original features and more background information about the data are not provided. 
Features V1, V2, … V28 are the principal components obtained with PCA, the only features which have not been transformed with PCA are 'Time' and 'Amount'.
Feature 'Time' contains the seconds elapsed between each transaction and the first transaction in the dataset. 
The feature 'Amount' is the transaction Amount, this feature can be used for example-dependant cost-sensitive learning. 
Feature 'Class' is the response variable and it takes value 1 in case of fraud and 0 otherwise.

## About the Project:
After loading the dataset, the first step was to perform an extensive Exploratory Data Analysis (EDA). Null values were checked as an initial step followed by
checking the amount of imbalanced categories with the target features. Count plot was used for this purpose. Then the normal amount and fraudulent amounts were 
analyzed and it was found that the fraudulent transaction amounts are very less compared to normal amount transactions. Histograms were plotted to validate this point.
Scatter plots showing the time of fraudulent and normal transactions were also plotted. Finally, to conclude this section a correlation heatmap including all the features
were plotted. 

The dataset was massive in size. To use the entire dataset requires a lot of computational time. So, I have taken a small sample (0.1%) of the dataset and on that I have performed the data splitting and model training. Data set was divided into Independent and Dependent features after sampling. Three unsupervised algorithms were applied inside a loop. The first is Isolation Forest (test accuracy 99.7%), Local Outliers Factors (test accuracy 99.6%) and One Class SVM (test accuracy 70%).
Clearly Isolation Forest out performed the others. Model was validated using accuracy score, precision, recall, error sum and f1 score. 

Some of the concluding remarks that I would like to make are as following:

1. Isolation Forest detected 73 errors versus Local Outlier Factor detecting 97 errors vs. SVM detecting 8516 errors
2. Isolation Forest has a 99.74% more accurate than LOF of 99.65% and SVM of 70.09
3. When comparing error precision & recall for 3 models , the Isolation Forest performed much better than the LOF as we can see that the detection of fraud cases is around 27 % versus LOF detection rate of just 2 % and SVM of 0%.
4. So overall Isolation Forest Method performed much better in determining the fraud cases which is around 30%.
5. We can also improve on this accuracy by increasing the sample size or use deep learning algorithms however at the cost of computational expense.We can also use complex anomaly detection models to get better accuracy in determining more fraudulent cases

### Isolation Forest Algorithm :
One of the newest techniques to detect anomalies is called Isolation Forests. The algorithm is based on the fact that anomalies are data points that are few and different. 
As a result of these properties, anomalies are susceptible to a mechanism called isolation.

This method is highly useful and is fundamentally different from all existing methods. It introduces the use of isolation as a more effective and efficient means to detect anomalies than the commonly used basic distance and density measures. Moreover, this method is an algorithm with a low linear time complexity and a small memory requirement. 
It builds a good performing model with a small number of trees using small sub-samples of fixed size, regardless of the size of a data set.

Typical machine learning methods tend to work better when the patterns they try to learn are balanced, meaning the same amount of good and bad behaviors are present in the dataset.

How Isolation Forests Work The Isolation Forest algorithm isolates observations by randomly selecting a feature and then randomly selecting a split value between the maximum and minimum values of the selected feature. The logic argument goes: isolating anomaly observations is easier because only a few conditions are needed to separate those cases from the normal observations. On the other hand, isolating normal observations require more conditions. Therefore, an anomaly score can be calculated as the number of conditions required to separate a given observation.

The way that the algorithm constructs the separation is by first creating isolation trees, or random decision trees. Then, the score is calculated as the path length to isolate the observation.

### Local Outlier Factor(LOF) Algorithm
The LOF algorithm is an unsupervised outlier detection method which computes the local density deviation of a given data point with respect to its neighbors. It considers as outlier samples that have a substantially lower density than their neighbors.

The number of neighbors considered, (parameter n_neighbors) is typically chosen 1) greater than the minimum number of objects a cluster has to contain, so that other objects can be local outliers relative to this cluster, and 2) smaller than the maximum number of close by objects that can potentially be local outliers. In practice, such informations are generally not available, and taking n_neighbors=20 appears to work well in general.
