# Quickstart 1.3 
# Automated Machine Learning

## Automated Machine Learning with Azure Machine Learning
Automated machine learning picks an algorithm and hyperparameters for you and generates a model ready for deployment. There are several options that you can use to configure automated machine learning experiments.

Configuration options available in automated machine learning:

- Select your experiment type: Classification, Regression or Time Series Forecasting
- Data source, formats, and fetch data
- Choose your compute target: local or remote
- Automated machine learning experiment settings
- Run an automated machine learning experiment
- Explore model metrics
- Register and deploy model

You can create and run automated machine learning experiments in code using the [Azure ML Python SDK](https://docs.microsoft.com/en-us/azure/machine-learning/service/how-to-configure-auto-train) or if you prefer a no code experience, you can also Create your automated machine learning experiments in the [Azure portal](https://docs.microsoft.com/en-us/azure/machine-learning/service/how-to-create-portal-experiments).

# Quickstart Overview
This quickstart is divided into two parts.

* In the first part, you learn how to create, run, and explore automated machine learning experiments in the Azure portal without a single line of code. Next, from within the Azure portal, you will register the best trained model, create the deployment image, and deploy a scoring web service on Azure Container Instance (ACI) to make predictions using the registered model.

* In the second part, you will access the deployed webservice using the Azure ML Python SDK and then test the scoring web service:     
    * by make direct calls on service object,</br>
    * by calling the service end point (Scoring URI) over http.

In this quickstart we will be building a regression model to predict Taxi Fares in New York City. We will use a preprocessed labeled training data with features such as number of passengers, trip distance, datetime, holiday information and weather information.

Please complete **Part 1** and **Part 2** specified in next pages to complete this quickstart.








