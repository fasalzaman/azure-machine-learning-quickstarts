# Quickstart 1.5
# Creating ONNX models with Azure Machine Learning
## Interoperability with ONNX
The [Open Neural Network Exchange](https://onnx.ai/) (ONNX) format is an open standard for representing machine learning models. ONNX is supported by a [community of partners](https://onnx.ai/supported-tools), including Microsoft, who create compatible frameworks and tools. Microsoft is committed to open and interoperable AI so that data scientists and developers can:

- Use the framework of their choice to create and train models
- Deploy models cross-platform with minimal integration work

Microsoft supports ONNX across its products including Azure and Windows to help you achieve these goals.

The interoperability you get with ONNX makes it possible to get great ideas into production faster. With ONNX, data scientists can choose their preferred framework for the job. Similarly, developers can spend less time getting models ready for production, and deploy across the cloud and edge.

You can create ONNX models from many frameworks, including PyTorch, Chainer, Microsoft Cognitive Toolkit (CNTK), MXNet, ML.Net, TensorFlow, Keras, SciKit-Learn, and more.
There is also an ecosystem of tools for visualizing and accelerating ONNX models. A number of pre-trained ONNX models are also available for common scenarios.
[ONNX models can be deployed](https://docs.microsoft.com/azure/machine-learning/service/how-to-build-deploy-onnx#deploy) to the cloud using Azure Machine Learning and ONNX Runtime. They can also be deployed to Windows 10 devices using [Windows ML](https://docs.microsoft.com/windows/ai/). They can even be deployed to other platforms using converters that are available from the ONNX community.

# Quickstart Overview
In this quickstart, you will take a previously trained deep learning model to classify the descriptions of car components provided by technicians as compliant or non-compliant, convert the trained model to ONNX, and deploy the model as a web service to make inferences. The model was trained using Keras with Tensorflow backend. You will also measure the speed of the ONNX runtime for making inferences and compare the speed of ONNX with Keras for making inferences.

## Before you begin

Confirm that you have completed quickstart: quickstart-1.0 for Visual Studio Code before you begin.

### Open the starting Python file
1. Start Visual Studio Code and open the folder: **`05-aml-onnx`**
2. From within Visual Studio Code click on the starting python file: **`onnx-AML.py`**
3. Confirm that you have setup **`azure_automl`** as your **interpreter**.
4. **`onnx-AML.py`** is the Python file you will step thru executing in this quickstart.
5. To execute each step click on **`Run Cell`** just above the block of code.

### Follow the instructions within the python file to complete the quickstart
