# Capstone

## Abstract 

Amplero is an Artificial Intelligence Marketing (AIM) company that enables business-to-consumer (B2C) marketers at global brands to optimize customer lifetime value at a scale that is not humanly possible. 

In the recent economy, subscription marketers are challenged to address the ever-changing behavior of customers. When a company interacts with its customer, it is important that they do it in a timely manner as it can have positive effects on user retention, engagement, and revenue.

Our objective is to predict whether a user will churn out of a network or not. 

## Project Summary

![alt text](https://github.com/niharikasharma/Capstone/blob/master/Images/Poster.png)

## License 

The code in this repository is released under the [MIT license](https://opensource.org/licenses/mit-license.php).

## Acknowledgement

We would like to express our gratitude to our sponsor and advisor, Dr.Luca Cazzanti and Prof. Megan Hazen, for there support, patience, and encouragement throughout the project. Their technical and editorial advice was essential to the completion of this project and has taught us innumerable lessons and insights on the workings of industrial research projects in general.

## Project Motivation 

We chose to do this project with Amplero as we wanted a chance to work with time series data and try our hand at time series prediction. We felt it would be a great learning experience and would be challenging at the same time. We realized that even a 1-3% decrease in user churn can tremendously increase in the revenue for the mobile network. A marketer would benefit greatly from our results and it could be used for targeted marketing as well. 

## Project structure

The package is organized as follows:
```

Capstone (master)
|
|----- CodeBase
|     |   
|     |     Data_SMS_0.csv.gz
|     |     README.md
|     |     Voting_Classifier.ipynb
|     |     entity_ids_used.csv
|     |     exploratory_analytics.ipynb
|     |     neural_network.ipynb
|     |     rechargeANDvoice.csv.gz
|     |----- Data_Extraction
|     |     |     social_TS.ipynb
|     |     |     state_recharge_voice_TS.ipynb
|     |     |     usage_TS.ipynb
|     |   
|----- Images
|     |     
|     |     Poster.png
|     |     KNN.png
|     |     SVC.png
|     |     VC.png
|     |     
|----- InterimReports
|     |     
|     |     Amplero-UW-Time_Series_data_set_summary.pdf
|     |     Interim Delivery.pdf
|     |     Pipeline Presentation.pdf
|     |     Project_Proposal.pdf
|     |     
|----- Poster
|     |     
|     |     Poster_v3.pdf
|     |     Poster_v3.pptx
|     |     
| LICENSE    
| README.md
```

## Data 

Note - We have not added the any time series .csv file. We are only uploading the compressed versions for Data_SMS_0.csv and rechargeANDvoice.csv as these are the only files under 100MB which is GitHub's file size limit. 

    Data_SMS_0.csv or Data_SMS_0.csv.gz (compressed) 
      Consist of the following time series -  
        Data in KB - CompactDataKBPerDayTimeSeries
        SMS - CompactSMSPerDayTimeSeries 

    rechargeANDvoice.csv or rechargeANDvoice.csv.gz (compressed)
      Consist of the following time series -  
        Amount and time of a pre-paid account recharge - RechargeTimeSeries
        State (Churned vs non-churned) - CarrierReportedSubscriptionStateDeltaTimeSeries
        Number of Voice calls per day - VoiceCallsPerDayTimeSeries

    Social1.csv or Social1.csv.gz (compressed)
      Consist of the following time series -  
        OutboundVoiceCountNetworkPageRankLast7DaysTimeSeries  
        OutboundVoiceCountNetworkPageRankQuantileLast7DaysTimeSeries  
        OutboundSMSNetworkPageRankLast7DaysTimeSeries  
        OutboundSMSNetworkPageRankQuantileLast7DaysTimeSeries  

    entity_ids_used.csv
      Consist of Entity IDs that we focused on for this project out of 1M users. 


## Results 

For testing the performance used the following performance metrics - 
    AUC, 
    Precision, 
    Recall, 
    Accuracy, and 
    F1 score.

Model Performance - 

1. The best result was using Voting Classifier with Best Models: Logistic Regression, RBF SVC and KNN with soft voting [2, 3, 1] having 80% as the accuracy. If we ignore inactive days feature, the accuracy of the model drops to 63%.

      Performance of KNN model varying K from 2 to 9 -

      ![alt text](https://github.com/niharikasharma/Capstone/blob/master/Images/KNN.png)

      Performance of SVC model varying the kernel - 

      ![alt text](https://github.com/niharikasharma/Capstone/blob/master/Images/SVC.png)

      Performance of Voting Classifier - 

      ![alt text](https://github.com/niharikasharma/Capstone/blob/master/Images/VC.png)

Note - Meaning x axis label in the above figure  - eg. - lr 1 svc 1 KN 1 means that Voting Classifier consist of Models: Logistic Regression, RBF SVC, and KNN with soft voting [1, 1, 1]


2. Neural Network model gave an accuracy of 75% when we consider the time series data till the date of churn. If we ignore 2 weeks of data just before churn, the accuracy of the model drops to 65%.
 
 
## Project Scope 

This project is very relevant to a large number of industries varying from the IT industry (AWS, Microsoft), Mobile networks (T-Mobile, ATnT), Media (HBO, Netflix, Comcast) to Retail market (Costco, Amazon). Currently, the project concentrates on Mobile network subscription data. The same methodology can be learned and applied to different industries dealing and handling analogous data. Such an analysis will provide a much deeper and richer problem to solve.

## Conclusion 
Number of inactive days seems to be a very predictor of churn. If we remove the number of inactive of days as a feature in the model, the performance of the model drops.

Voting Classifier and Neural network models can enable mobile networks to identify users that may churn in the future. We think this information is crucial and can be used to provide tailor made promotions to users so that they don’t churn from the network.


## Reproducibility

For running and replicating the results and algorithm, install all the packages correctly as mentioned in the Jupyter Notebook and run the Jupyter Notebook.

You can use a larger dataset or a different dataset but make sure that the column name and column type remains the same. Any other change in the new dataset might reduce the chances of reproducibility.



## Python Libraries used for this project 
	Matplotlib - for data visualization
	Numpy - for data processing
	Pandas - for data processing
	Scikit learn - for modelling 
	DataTime - for date formatting
	GZip - for handling compressed data
	pprint - provides a capability to pretty-print 
	io -  for working with streams 
	boto3 - for AWS S3 connections 
	json - for handling data in json format
	StringIO - for Reading and writing strings as files 
	statistics - for exploratory analytics 
	statsmodels - for experimenting with arima model

