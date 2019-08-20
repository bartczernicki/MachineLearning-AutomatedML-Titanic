<a name="Title"></a>
# Walkthrough - Building a binary classifier using the Titanic DataSet
Azure (Azure Portal) Automated ML walkthrough using the Titanic Dataset


![Titanic Picture](https://upload.wikimedia.org/wikipedia/commons/thumb/f/fd/RMS_Titanic_3.jpg/600px-RMS_Titanic_3.jpg)

<a name="Overview"></a>
## Overview ##
**Microsoft Automated ML** allows non-professional data scientists (aka "citizen data scientists") to build various types of custom machine learning models using a wizard-driven approach of selecting declerative configuration options and allowing the Automated ML engine to perform all of the complex ML tasks (i.e. pre-processing, algorithm selection, hyperparameter tuning, ensembling, code generation, model conversion/export, deployment) all behind the scenes and largely hidden from the user.

This walkthrough demonstrates how-to build an binary classifier (classification model) using Microsoft Automated ML.  This walkthrough includes step by step instructions using the Azure portal & the Azure Machine Learning service; requiring zero code.

<a name="Objectives"></a>
## Objectives ##

- Create an Azure Machine Learning service Workspace
- Create custom Azure compute, where the model training will be processed
- Upload the Titanic data set (small CSV file)
- Configure the Automated ML experiment
- Evaluate the Performance of the image classifier
- Evaluate operationalization options (model export, deployment)
- Next Steps

<a name="Prerequisites"></a>
## Prerequisites ##

- An active internet connection & a browser
- An Azure subscription is **REQUIRED**.  However, you can use ANY Azure subscription type (free trial, MSDN, Enterprise etc.) that you have access to.
- Access to the main Azure portal

<a name="Intended Audience"></a>
## Intended Audience ##

This lab is intended for aspiring AI professionals that would like to learn more about the basics of machine learning, Auzre ML or are interested in the AutoML paradigm implemented using Automated ML.


### Task 1: Create a new Azure ML Experiment & Automed ML Experiment ###

1. Download the **Titanic Data set (CSV)** that are located in the Data directory in this repository:
https://github.com/bartczernicki/MachineLearning-AutomatedML-Titanic

2. Navigate to the main Azure portal **https://portal.azure.com** and sign-in.  After signing-in, select **Create a resource** from the top-left menu option.  Type in **Azure Machine Learning** in the Search the Marketplace search dialog and then click the enter button.  A dialog (shown below) will appear.  Select the **Create** button.
<p align="center">
  <img src="https://github.com/bartczernicki/MachineLearning-AutomatedML-Titanic/blob/master/WalkthroughImages/AutomatedML-CreateWorkspace.png">
</p>


3. After selecting to create the workspace, it will take a several seconds (up to a minute or so) to create the workspace.  You will notice the image below as the workspace is being created.
<p align="center">
  <img src="https://github.com/bartczernicki/MachineLearning-AutomatedML-Titanic/blob/master/WalkthroughImages/AutomatedML-DeploymentOnYourWay.png">
</p>

4. After the deployment finishes, you will see a dialog (screenshot shown below) letting you knowthe deployment of the workspace has finished.  Click the **Go to resource** button to go to the Azure ML Workspace.

5. The Azure Machine Learning service consists of a portfolio of machine learning services.  In the Authoring group, select the **Automated machine learning** option to continute onto that service (screenshot shown below)
<p align="center">
  <img src="https://github.com/bartczernicki/MachineLearning-AutomatedML-Titanic/blob/master/WalkthroughImages/AutomatedML-SelectAutomatedMachineLearning.png">
</p>

6. Brand new Azure ML service workspaces will have no experiments and shown the dialog below.  Click the **Create experiment** button (screenshot shown below)
<p align="center">
  <img src="https://github.com/bartczernicki/MachineLearning-AutomatedML-Titanic/blob/master/WalkthroughImages/AutomatedML-CreateExperiment.png">
</p>


7. You will now be shown a Create experiment dialog (screenshot shown below)
- In the Name area, fill in the name of the experiment.  In this example, the name **TitanicSurvivalClassifier** was used.
- If you do not have provisioned ML compute, select the **Create a new compute** link.
<p align="center">
  <img src="https://github.com/bartczernicki/MachineLearning-AutomatedML-Titanic/blob/master/WalkthroughImages/AutomatedML-CreateExperimentDialog.png">
</p>
