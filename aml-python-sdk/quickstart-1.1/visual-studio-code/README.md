# Quickstart 1.1 
# Azure Machine Learning Pipelines
## What are machine learning pipelines?
Using [Azure Machine Learning SDK for Python](https://docs.microsoft.com/en-us/python/api/azureml-pipeline-core/?view=azure-ml-py), data scientists, data engineers, and IT professionals can collaborate on the steps involved in:
* Data preparation, such as normalizations and transformations
* Model training
* Model evaluation
* Deployment

The following diagram shows an example pipeline:

![azure machine learning piplines](./images/pipelines.png)

# Quickstart Overview
The goal of this quickstart is to build a pipeline that demonstrate the basic data science workflow of data preparation, model training, and predictions. Azure Machine Learning, allows you to define distinct steps and make it possible to rerun only the steps you need as you tweak and test your workflow.

In this quickstart, we will be using a subset of NYC Taxi & Limousine Commission - green taxi trip records available from [Azure Open Datasets](https://azure.microsoft.com/en-us/services/open-datasets/). The data is enriched with holiday and weather data. The goal is to train a regression model to predict taxi fares in New York City based on input features such as, number of passengers, trip distance, datetime, holiday information and weather information.

The machine learning pipeline in this quickstart is organized into three steps:

- **Preprocess Training and Input Data:** We want to preprocess the data to better represent the datetime features, such as hours of the day, and day of the week to capture the cyclical nature of these features.

- **Model Training:** We will use data transformations and the GradientBoostingRegressor algorithm from the scikit-learn library to train a regression model. The trained model will be saved for later making predictions.

- **Model Inference:** In this scenario, we want to support **bulk predictions**. Each time an input file is uploaded to a data store, we want to initiate bulk model predictions on the input data. However, before we do model predictions, we will reuse the preprocess data step to process input data, and then make predictions on the processed data using the trained model.

Each of these pipelines is going to have implicit data dependencies and the example will demonstrate how AML make it possible to reuse previously completed steps and run only the modified or new steps in your pipeline.

The pipelines will be run on the Azure Machine Learning compute.

## Before you begin

Confirm that you have completed quickstart-1.0 for Visual Studio Code before you begin.

### Open the starting Python file
1. **Start** Visual Studio Code and **open** the folder: **`01-aml-pipelines`**
2. From within Visual Studio Code click on the starting python file: **`pipelines-AML.py`**.
3. Confirm that you have setup **`azure_automl`** as your **interpreter**.
4. **`pipelines-AML.py`** is the Python file you will step thru executing in this lab.
5. To execute each step click on **`Run Cell`** just above the block of code. 

### Follow the instructions within the python file to complete the lab
