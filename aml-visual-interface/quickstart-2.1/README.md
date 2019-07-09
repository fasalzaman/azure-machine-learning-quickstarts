# Quickstart 1.0 
# Azure Machine Learning Visual Interface
In this quickstart, we will be using a subset of NYC Taxi & Limousine Commission - green taxi trip records available from [Azure Open Datasets](https://azure.microsoft.com/en-us/services/open-datasets/). The data is enriched with holiday and weather data. Based on the enriched dataset, we will learn to use the Azure Machine Learning Graphical Interface to process data, build, train, score, and evaluate a regression model to predict NYC taxi fares. To train the model, we will create Azure Machine Learning Compute resource. We will also learn to deploy the model as a scoring webservice to Azure Kubernetes Compute. Finally, we will test the deployed webservice, and review how to consume the deployed web service. We will do all of this from the Azure Machine Learning Visual Interface without writing a single line of code.

## Before you begin

- Download the training data file [nyc-taxi-sample-data.csv](https://quickstartsws9073123377.blob.core.windows.net/azureml-blobstore-0d1c4218-a5f9-418b-bf55-902b65277b85/quickstarts/nyc-taxi-data/nyc-taxi-sample-data.csv) on your local disk.

# Exercise 1: Upload Training Dataset in Visual Interface

## Task 1: Open Visual Interface

1. Login to [Azure Portal](https://portal.azure.com). Navigate to the machine learning workspace: `quick-starts-ws`
2. Select `Visual interface` in the left navigation bar
3. Select on **Launch visual interface**

   <img src="./images/01.png" width="70%" height="70%" title="Launch visual interface" border="15">

## Task 2: Upload Training Dataset

1. From within Visual Interface select **+ New**

   <img src="./images/02_1.png" width="70%" height="70%" title="Click on + New" border="15">

2. From the left navigation select **Datasets**
3. From **New Datasets** select **Upload from Local File**

   <img src="./images/02_2.png" width="70%" height="70%" title="Click on Upload from Local File" border="15">

4. Use **Choose File** to select `nyc-taxi-sample-data.csv` from your local disk and then select **Ok**

   <img src="./images/02_3.png" width="70%" height="70%" title="Click on Ok" border="15">

# Exercise 2: Define Experiment

## Task 1: Create New Blank Experiment

1. From within Visual Interface select **+ New**
2. Select **+ Blank Experiment**

   <img src="./images/03_1.png" width="70%" height="70%" title="Click on + Blank Experiment" border="15">

## Task 2: Select Dataset

1. Expand **Saved Datasets, My Datasets** in the left navigation

   <img src="./images/03_2.png" width="70%" height="70%" title="Expand My Datasets" border="15">

2. Drag and drop the dataset `nyc-taxi-sample-data.csv` on to the canvas

   <img src="./images/03_3.png" width="70%" height="70%" title="Drag and Drop My Dataset" border="15">

## Task 3: Select Columns in Dataset

1. Open **Data Transformation, Manipulation section** section in the left panel
2. Drag and drop **Select Columns in Dataset** module on to the canvas
3. Select the added `Select Columns in Dataset` module
4. Click on **Edit columns** in the right panel

   <img src="./images/04_1.png" width="70%" height="70%" title="Select Columns in Dataset Module" border="15">

5. Select **Begin With All Columns** and then in the drop down select **Exclude**. Enter the column name `vendorID` in the textbox and then select **Ok**.

   <img src="./images/04_2.png" width="70%" height="70%" title="Exclude vendorID column" border="15">
   
## Task 4: Clean Missing Data
   
1. Add **Clean Missing Data** module
2. Connect the `Dataset` to `Select Columns in Dataset` module
3. Connect the `Select Columns in Dataset` to `Clean Missing Data` module
4. Select the added  `Clean Missing Data` module
5. Select `Replace with mean` as `Cleaning mode` in the right panel
6. Select on **Edit columns** in the right panel

   <img src="./images/04_3.png" width="70%" height="70%" title="Clean Missing Data Module" border="15">

7. Exclude the two non-numeric data columns `normalizeHolidayName` and `isPaidTimeOff` and then select **Ok**

   <img src="./images/04_4.png" width="70%" height="70%" title="Exclude non-numeric columns" border="15">

## Task 5: Split the Training Data

1. Expand **Data Transformation, Sample and Split** in the left navigation and add the **Split Data** module 
2. Connect the first output from `Clean Missing Data` module to the `Split Data` module
3. Select the **Split Data** module
4. Set `0.7` as the fraction of rows in first output

   <img src="./images/04_5.png" width="70%" height="70%" title="Split Data Module" border="15">

*Note that you can run the experiment at any point to peek at the outputs and activities. Running experiments also generates metadata that is available for downstream activities such selecting column names from a list in selection dialogs.*

## Task 6: Initialize Regression Model

1. Expand **Machine Learning, Initialize Model, Regression** section in the left panel
2. Add the **Boosted Decision Tree Regression** module on to the canvas
3. Configure your model parameters: `Minimum number of samples per node: 1` and `Learning rate: 0.1`

   <img src="./images/05_1.png" width="70%" height="70%" title="Boosted Decision Tree Regression Module"  border="15">

## Task 7: Setup Train Model Module

1. Expand **Machine Learning, Train** section in the left panel
2. Add **Train Model** module on to the canvas

   <img src="./images/06_1.png" width="70%" height="70%" title="Train Model Module"  border="15">
   
3. Select on **Edit columns** in the right panel to setup your `Label or Target column`
4. Select `totalAmount` as your target column, and then select **Ok**

   <img src="./images/06_2.png" width="70%" height="70%" title="Setup totalAmount as target column"  border="15">
   
## Task 8: Make Connections to Train Module

1. Connect the `Boosted Decision Tree Regression` module to `Train Model` module
2. Connect the first output of `Split Data` module to `Train Model` module

   <img src="./images/07_1a.png" width="70%" height="70%" title="Connect Train Module"  border="15">

## Task 9: Setup Score Model Module

1. Expand **Machine Learning, Score** section in the left panel
2. Add **Score Model** module on to the canvas
3. Connect the `Train Model` module to the first input of the `Score Model` module
4. Connect the second output of `Split Data` module to the second input of the `Score Model` module

   <img src="./images/07_1b.png" width="70%" height="70%" title="Connect Score Module"  border="15">

*Note that `Split Data` module will feed data for both model training and model scoring. The first output (0.7 fraction) will connect with the `Train Model` module and the second output (0.3 fraction) will connect with the `Score Model` module.*
   
## Task 10: Setup Evaluate Model Module

1. Open **Machine Learning, Evaluate** section in the left panel
2. Add **Evaluate Model** module on to the canvas
3. Connect the `Score Model` module to `Evaluate Model` module

   <img src="./images/07_2.png" width="70%" height="70%" title="Evaluate Model Module"  border="15">

# Exercise 3: Run Experiment

## Task 1: Select Run Experiment

1. From the experiment select **Run**

   <img src="./images/08_1.png" width="70%" height="70%" title="Click on Run Experiment"  border="15">
   
## Task 2: Select Compute to Run Experiment
   
1. Note that you can create a new **Compute Target** directly from **Visual Interface**
2. Select **Select existing**
3. Select **qs-compute** (this is the compute target we created in `quickstart-2.0`)
4. Select **Run**
5. The experiment will run for about 8-10 minutes 

   <img src="./images/08_2.png" width="70%" height="70%" title="Select Compute and Run Experiment"  border="15">

# Exercise 4: Visualize Results

## Task 1: Visualize the Model Predictions

1. Wait for model training to be complete
2. Right click on **Score Model** module and select **Scored dataset -> Visualize**

   <img src="./images/09_1.png" width="70%" height="70%" title="Visualize the Model Predictions" border="15">
   
3. Compare the predicted `predicted taxi fares` to the `target taxi fares`
4. You can also observe the predicted value distribution when you select the `Scored Labels` column 

   <img src="./images/09_2.png" width="70%" height="70%" title="Compare prediction to actual values" border="15">

## Task 2: Visualize the Evaluation Results

1. Right click on **Evaluate Model** module and select **Evaluation results -> Visualize**

   <img src="./images/10_1.png" width="70%" height="70%" title="Visualize the Model Evaluation" border="15">
   
2. Observe the Model Evaluation Metrics such as **Root Mean Squared Error**

   <img src="./images/10_2.png" width="70%" height="70%" title="Model Evaluation Metrics" border="15">

# Exercise 5: View Experiment Run History

## Task 1: Go to Run History

1. From the experiment select **Run History**

   <img src="./images/11_1.png" width="70%" height="70%" title="Go to Run History" border="15">
   
## Task 2: Return to Experiment
   
1. Go back to the Experiment by selecting the Run History item with `Editable` state

   <img src="./images/11_2.png" width="70%" title="Go back to the experiment">

# Exercise 6: Save Trained Model

## Task 1: Save Trained Model

1. Right click on the `Train Model` module and select **Trained model -> Save as Trained Model**

   <img src="./images/12_1.png" width="70%" height="70%" title="Right click on the Train Model module" border="15">
   
2. Provide `model name` and select **Ok**

   <img src="./images/12_2.png" width="70%" height="70%" title="Save the Trained Model" border="15">

# Exercise 7: Run Predictive Experiment

## Task 1: Create Predictive Experiment

1. Observe the saved model appears in the `Trained Models` section
2. Select **Create Predictive Experiment**
3. This will create the `Predictive Experiment` in a new tab named: **Predictive experiment**

   <img src="./images/13_1.png" width="70%" height="70%" title="Create Predictive Experiment" border="15">

## Task 2: Run Predictive Experiment

1. From the **Predictive experiment** tab, select **Run**
2. Select the existing compute target to run the predictive experiment
3. It will take about 4-5 minutes to run the predictive experiment

   <img src="./images/13_2.png" width="70%" height="70%" title="Click on Run" border="15">

# Exercise 8: Deploy Web Service on Kubernetes Service Compute

## Task 1: Deploy Web Service

1. From the **Predictive experiment** tab, select **Deploy Web Service**

   <img src="./images/14_1.png" width="70%" height="70%" title="Deploy Web Service" border="15">
   
## Task 2: Select Compute Target to Deploy Web Service
   
1. Select the existing Kubernetes Service compute, and select **Deploy**

   <img src="./images/14_2.png" width="70%" height="70%" title="Deploy Web Service" border="15">

# Exercise 9: Consume the Deployed Web Service

## Task 1: Open the Deployed Web Service

1. Navigate to the Web Services section of the Visual Interface

2. Select the deployed Web Service

   <img src="./images/15_1.png" width="70%" height="70%" title="Open the Web Service" border="15">
   
## Task 2: Test the Web Service

1. Fill in the input data for predicting the NYC Taxi Fare, and select **Test**

## Task 3: Observe Predictions

1. Select the **Raw** test results and observe the predicted NYC Taxi Fare: **Scored Labels**

   <img src="./images/15_2.png" width="70%" height="70%" title="Test the Web Service" border="15">

## Task 4: Review how to Consume the Deployed Web Service

1. Navigate to the **Consume** section of the Web Service
2. Observe the provided sample code in C#, Python, and R to consume the Web Service

   <img src="./images/16_1.png" width="70%" height="70%" title="Consume the Deployed Web Service" border="15">

# Exercise 10: Challenge Experiment

Is there another regression model that can give us an improved evaluation score on the `Root Mean Square Error (RMSE)` metric?  The `Boosted Decision Tree Regression` gave us an RMSE score of **4.17**. Experiment with other models like the `Neural Net Regression` model and evaluate if you can train a better performing model on the RMSE metric. Please note that the objective is to minimize the RMSE score.

# Exercise 11: Cleanup Resources

## Task 1: Delete Web Service

1. Go to Azure Portal and navigate to the Deployments section of the workspace
2. **Delete** the deployed Web Service

   <img src="./images/17_1.png" width="70%" height="70%" title="Delete the deployed Web Service" border="15">

## Task 2: Delete Compute Targets

1. Navigate to **Compute** section
2. **Delete** both the compute targets created for this quickstart - one at a time

   <img src="./images/17_2.png" width="70%" height="70%" title="Delete the Compute Targets" border="15">

