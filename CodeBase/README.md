# DATA 591 A Wi 18: Data Science Capstone II- Project Implementation
# README.md

## Data 

Note - We have not added any time series .csv file. We are only uploading the compressed versions for Data_SMS_0.csv and rechargeANDvoice.csv as these are the only files under 100MB which is GitHub's file size limit. 

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


## Data_Extraction (Data_Extraction directory)

	social_TS.ipynb
		Extract Social data and save it in Social1.csv.gz compressed file. Extracted from the social*.jsonish.gz files that contains time series of social network attributes for each entity. The social networks are constructed from the voice and SMS traffic.

	state_recharge_voice_TS.ipynb
		Extract state (churn/non-churn), voice call, recharge data and save it in rechargeANDvoice.csv.gz  compressed file. Extracted from the state_recharge_etc.jsonish.gz.

	usage_TS.ipynb
		Extract usage(data in KB and SMS) data and save it in Data_SMS_0.csv.gz compressed file. Extracted from the usage*.jsonish.gz files that contains usage information for each entity. The usage is according to SMS, Data, and Voice. These time series are nested. The idea is that SMS usage time series can be sub-divided in component time series according to a finer-grained classification of usage: inbound SMS, outbound SMS, outbound SMS to international recipients, inbound SMS from international senders, etc. and similarly for other dimensions of usage.


## Model
	Voting Classifier - Voting_Classifier.ipynb
		This file contains code for following components:
		1. Data clean up 
		2. Feature selection 
		3. Finding churners and non-churners 
		4. Rejecting users who have insufficient data and based on certain criteria
		5. Experiment with different models like KNN, SVC 
		6. Voting Classifier
			Consists of three different models -
			Logistic Regression, SVC [kernel="rbf], KNN [n=5]
			Experimented with the feature vector (with & without inactive days)
			Selected different K size for KNN
			Experimented with RBF, linear and poly kernel for SVC

		The best result is using Voting Classifier with Best Models: RBF SVC, Logistic Regression, and KNN with soft voting [3, 2, 1] having ~0.80 as the final score. 

	Neural Network - neural_network.ipynb
        	This file contains code for following components:
	        1. Data Cleaning
	        2. Feature extraction - converting the timeseries to a feature representation
	        3. Undersampling the majority class
	        4. Splitting data into train/test split
	        5. Building a neural network model
	        6. Testing the performance - AUC, precision, recall


## Python Libraries used for this project - 
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


