# Azure Machine Learning Service Quickstarts

[Azure Machine Learning Service](https://docs.microsoft.com/en-us/azure/machine-learning/service/overview-what-is-azure-ml) is a cloud service for machine learning that support training, deploying, managing, and operationalizing (MLOps) models in Azure using Python SDK and CLI. Azure Machine Learning service also provides a visual interface (preview) to quickly, prepare data, and train machine learning models.

The Quickstarts are grouped into two parts: (1) Quickstarts for [Azure Machine Learning Python SDK](https://docs.microsoft.com/en-us/python/api/overview/azure/ml/intro?view=azure-ml-py), and (2) Quickstart for [Azure Machine Learning Visual Interface](https://docs.microsoft.com/en-us/azure/machine-learning/service/ui-quickstart-run-experiment).

## 1. Azure Machine Learning Python SDK

The following set of quickstarts demonstrate a key set of Azure Machine Learning Services and provides instructions for you to preform them using a Python environment of Visual Studio Code.

### 1.0 Setting up your environment

This provides the instructions to get started with the lab.

### 1.1 Azure Machine Learning Pipelines

The goal of this quickstart is to build machine learning pipelines using Azure Machine Learning Python SDK that demonstrate the basic data science workflow of data preparation, model training, and predictions.

### 1.2 MLOps with Azure Machine Learning Service and Azure DevOps

The goal of this quickstart is to build a simple use case that shows how you can operationalize your machine learning models that leverages the Azure DevOps Machine Learning extension, CLI extension for Azure Machine Learning service, and Azure Machine Learning Pipelines that integrate with Azure DevOps CI/CD and deployment workflows.

### 1.3 Automated Machine Learning

In this quickstart, you will learn how to create, train, evaluate, and deploy automated machine learning models in the Azure portal without a single line of code.

### 1.4 Deep Learning with Azure Machine Learning

In this quickstart, you will train a deep learning model to classify the descriptions of car components as compliant or non-compliant. You will train the model on Azure Machine Learning Compute Cluster, download the trained model to your local computer, and make predictions.

### 1.5 Creating ONNX models with Azure Machine Learning

In this quickstart, your will convert a Deep Learning model you trained in **quickstart-1.4** to ONNX format and deploy the ONNX model as a web service to make inferences. You will also measure the speed of the ONNX runtime for making inferences and compare the speed of ONNX with Keras for making inferences.

### 1.6 Model Interpretability with Azure Machine Learning

The goal of this quickstart is to show Model interpretability with Azure Machine Learning service. You will learn how to explain why your model made the prediction it made by using the Azure Machine Learning Interpretability SDK. You will learn to understand both global and local explainability of your model. Finally, you will also learn how to deploy the explainer along with the model to be used at scoring time to make predictions and provide local explanations.

## 2. Azure Machine Learning Visual Interface

Azure Machine Learning Visual Interface gives you a cloud-based interactive, visual workspace that you can use to easily and quickly prep data, train and deploy machine learning models. It supports Azure Machine Learning compute, GPU or CPU. Machine Learning Visual Interface also supports publishing models as web services on Azure Kubernetes Service that can easily be consumed by other applications. To use Azure Machine Learning Studio, you do not need programming experience and this quickstart will walk you through an exercise that will show how to process training data, create a model, train, score, and evaluate the model and finally deploy the trained model as a web service.

### 2.0 Setting up your environment

This provides the instructions to get started with the lab.

### 2.1 Azure Machine Learning Visual Interface

In this quickstart, we will be using a subset of NYC Taxi & Limousine Commission - green taxi trip records available from [Azure Open Datasets](https://azure.microsoft.com/en-us/services/open-datasets/). The data is enriched with holiday and weather data. Based on the enriched dataset, we will learn to use the Azure Machine Learning Graphical Interface to process data, build, train, score, and evaluate a regression model to predict NYC taxi fares. To train the model, we will create Azure Machine Learning Compute resource. We will also learn to deploy the model as a scoring webservice to Azure Kubernetes Compute. Finally, we will test the deployed webservice, and review how to consume the deployed web service. We will do all of this from the Azure Machine Learning Visual Interface without writing a single line of code.
