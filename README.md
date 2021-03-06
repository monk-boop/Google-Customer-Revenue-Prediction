# Google-Customer-Revenue-Prediction
A top 10% solution to the kaggle competition where we are required to predict the revenue generated by a returning cutomer in the G-Store.
- The 80/20 rule has proven true for many businesses–only a small percentage of customers produce most of the revenue. As such, marketing teams are challenged to make appropriate investments in promotional strategies.
- In this case study, we analyze a Google Merchandise Store (also known as GStore, where Google swag is sold) customer dataset to predict revenue per customer. Hopefully, the outcome will be more actionable operational changes and a better use of marketing budgets for those companies who choose to use data analysis on top of GA data.
## Evaluation
Submissions are scored on the root mean squared error. RMSE is defined as:

$\begin{align}\textrm{RMSE} = \sqrt{\frac{1}{n} \sum_{i=1}^{n} (y_i - \hat{y}_i)^2},\end{align}$

where y hat is the natural log of the predicted revenue for a customer and y is the natural log of the actual summed revenue value plus one.
<h3>About the dataset:</h3>

We are given two datasets - <b>train.csv</b> and <b>test.csv</b>

Each row in the datasets is one visit to the store. We are predicting the natural log of the sum of all transactions per user.

The data fields in the given files are

- fullVisitorId- A unique identifier for each user of the Google Merchandise Store.
- channelGrouping - The channel via which the user came to the Store.
- date - The date on which the user visited the Store.
- device - The specifications for the device used to access the Store.
- geoNetwork - This section contains information about the geography of the user.
- sessionId - A unique identifier for this visit to the store.
- socialEngagementType - Engagement type, either "Socially Engaged" or "Not Socially Engaged".
- totals - This section contains aggregate values across the session.
- trafficSource - This section contains information about the Traffic Source from which the session originated.
- visitId - An identifier for this session. This is part of the value usually stored as the _utmb cookie. This is only unique to the user. For a completely unique ID, you should use a combination of fullVisitorId and visitId.
- visitNumber - The session number for this user. If this is the first session, then this is set to 1.
- visitStartTime - The timestamp (expressed as POSIX time).
- Also it is important to note that some of the fields are in json format.
### What am I predicting?
- In the Kaggle competition, we have to take all the unique fullVisitorId's from the test dataset and predict the <b>Total Revenue </b> for each full visitor ID for their future transactions of 1st December 2018 - 31st January 2019.
-  Due to the formatting of fullVisitorId, we must load the Id's as strings in order for all Id's to be properly unique!
- Since We'ew not doing this competition as a kaggle competition, we will do all of our predictions on the test_v2.csv data using train_v2.csv as training data.
### Problem Trnasformation
- We transform this problem into a non-time series regression problem. This is because we have to predict for each user the estimated revenue that the user is likely to generate. And since a user who visits once may not visit again, we will solve this as a normal - regression type problem.
### Constraints
- For this problem, there are no constraints as such. The results of this problem will help GStore marketing team make better decisions when it comes to marketing practices. However, wrong information can lead to mismanagement of money allocation in marketing practices.
