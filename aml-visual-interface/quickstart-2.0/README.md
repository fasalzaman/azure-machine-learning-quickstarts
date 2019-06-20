# 2. Azure Machine Learning Visual Interface

Azure Machine Learning Visual Interface gives you a cloud-based interactive, visual workspace that you can use to easily and quickly prep data, train and deploy machine learning models. It supports Azure Machine Learning compute, GPU or CPU. Machine Learning Visual Interface also supports publishing models as web services on Azure Kubernetes Service that can easily be consumed by other applications. To use Azure Machine Learning Studio, you do not need programming experience and this quickstart will walk you through an exercise that will show how to process training data, create a model, train, score, and evaluate the model and finally deploy the trained model as a web service.

# 2.0 Setting up your environment 

- You can use the resource group named: `QuickStarts` for this lab.

- Create an Azure Machine Learning service workspace named: `quick-starts-ws`. See [Create an Azure Machine Learning Service Workspace](https://docs.microsoft.com/en-us/azure/machine-learning/service/setup-create-workspace) for details on how to create the workspace.

Next, we will upfront create two Azure Machine Learning Computes, one for running machine learning experiments and the other for deploying trained models. Creating computes can take upto 5 minutes, thus we can start the creation and move on to the quickstart to conserve time. 


## Task 1: Create Azure Machine Learning Compute

Create a compute target in the workspace `quick-starts-ws` to run your Azure Machine Learning experiments.

1. Navigate to your workspace `quick-starts-ws` and select `Compute` from the `Assets` section and then select on **Add Compute**:

   <img src="./images/01.png" width="70%" height="70%" title="Click on Add Compute">

2. On the **Add Compute**, enter the following and then select **Create**:

   a. Compute name: `qs-compute`
   
   b. Compute type: `Machine Learning Compute`
   
   c. Region: `Select your region`
   
   d. Virtual machine size: `Standard_D2_v2`
   
   e. Minimum number of nodes: `1`
   
   f. Maximum number of nodes: `1`
   
   <img src="./images/02.png" width="70%" height="70%" title="Create a Machine Learning Compute">


## Task 2: Create Kubernetes Service Compute

Next, we will create a Kubernetes Service Compute to publish the trained model as web service.

1. Navigate to your workspace `quick-starts-ws` and select `Compute` from the `Assets` section and then select on **Add Compute**

2. On the **Add Compute**, enter the following and then select **Create**:

   a. Compute name: `nyc-taxi`
   
   b. Compute type: `Kubernetes Service`
   
   c. Region: `Select your region`
   
   d. Virtual machine size: `Standard_D3_v2`
   
   e. Number of nodes: `3`
   
   <img src="./images/03.png" width="70%" height="70%" title="Create Kubernetes Service Compute">

## Next, follow the steps as outlined for quickstart [Azure Machine Learning Visual Interface](../../aml-visual-interface/quickstart-2.1/README.md)
