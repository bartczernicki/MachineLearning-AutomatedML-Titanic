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

- Make yourself familiar with the Titanic experiment.  For an interactive demo, navigate to: https://demos.datasciencedojo.com/demo/titanic/
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
  <img width=800 height=517 src="https://github.com/bartczernicki/MachineLearning-AutomatedML-Titanic/blob/master/WalkthroughImages/AutomatedML-SelectAutomatedMachineLearning.png">
</p>

6. Brand new Azure ML service workspaces will have no experiments and shown the dialog below.  Click the **Create experiment** button (screenshot shown below)
<p align="center">
  <img width=700 height=257 src="https://github.com/bartczernicki/MachineLearning-AutomatedML-Titanic/blob/master/WalkthroughImages/AutomatedML-CreateExperiment.png">
</p>


7. You will now be shown a Create experiment dialog (screenshot shown below)
- In the Name area, fill in the name of the experiment.  In this example, the name **TitanicSurvivalClassifier** was used.
- If you do not have provisioned ML compute, select the **Create a new compute** link.
<p align="center">
  <img src="https://github.com/bartczernicki/MachineLearning-AutomatedML-Titanic/blob/master/WalkthroughImages/AutomatedML-CreateExperimentDialog.png">
</p>

8. The "Create a New Compute" Dialog will appear.  Fill out the following information (screenshot shown below):
- In the Name field, fill out the name of the compute.  In this example, the name **demoCompute** is shown.
- Select the **STANDARD_D1_V2--..."** compute option.  This compute will be run on a VM with 1 vCPU core & 3.5gig of memory.  This is plenty for the small Titanic CSV data set.
- Expand the **Additional Settings** options
- Change the **Maximum number of nodes** from 6 to 1.  This will prevent from more than a single VM being created when the compute is being used.
- When finished, select the **Create** button.
<p align="center">
  <img width=800 height=684 src="https://github.com/bartczernicki/MachineLearning-AutomatedML-Titanic/blob/master/WalkthroughImages/AutomatedML-CreateANewCompute.png">
</p>


9. The compute will take several minutes to complete.  When creating the compute, the dialog will appear similar to the dialog below.
<p align="center">
  <img src="https://github.com/bartczernicki/MachineLearning-AutomatedML-Titanic/blob/master/WalkthroughImages/AutomatedML-CreatingANewCompute.png">
</p>


10. After the compute has finished provisioning, you will be taken back to the "Create a new automated machine learning experiment" dialog.  Notice that the compute dropdown is now filled in with the name provided in step #8.  In this example, that was "demoCompute".  Click the **Next** button to proceed.
<p align="center">
  <img width=800 height=323 src="https://github.com/bartczernicki/MachineLearning-AutomatedML-Titanic/blob/master/WalkthroughImages/AutomatedML-CreateExperimentDialog2.png">
</p>


11. Additional storage information is filled in and will be created.  Notice that there is an **Upload** button on the bottom right.  Click the **Upload** button and select the **TitanicDataSet.csv** file.  After this is uploaded, select the file (shown in the screenshot below).
<p align="center">
  <img src="https://github.com/bartczernicki/MachineLearning-AutomatedML-Titanic/blob/master/WalkthroughImages/AutomatedML-CreateExperimentSelectDataSet.png">
</p>

12. The CSV schema and the names (using the top row) of the Titanic data set is inferred.  You can now configure the data & the experiment further.  In machine learning, as a general rule you will want to remove columns that do not have any predictive power.  Columns like ID columns, names or unique idenitifiers (i.e. receipt numbers) are poor choices for ML models.  In the dialog, select the radio button and remove the following three columns:
- PASSENGERID
- NAME
- TICKET

13. Below in the same dialog, in the **Target Column** you want to select the column that you want to predict in the experiment.  In this experiment, you want to predict survival of the Titanic.  Therefore, select the **Survived** column.

14. In the same dialog, expand the **Advanced Settings** options.  Automated ML can run many iterations over several hours or days.  However, for this experiment we will want to get quick results.  Therefore, change the following settings:
- Change **Training job time (minutes)** to 4 (4 minutes)
- Change **Max number of iterations** to 10 (10 iterations)
Note: Whichever occurs first (training time or max iterations) will cause the experiment job to terminate first.
(Screenshot below shows the complete setting in steps #11 - #14)
<p align="center">
  <img width=800 height=707 src="https://github.com/bartczernicki/MachineLearning-AutomatedML-Titanic/blob/master/WalkthroughImages/AutomatedML-CreateExperimentPreview.png">
</p>


15. Click the **Start** button to start the experiment job.  This will take up to 15 minutes to complete. Why does it take so long?
- Compute VMs leverage cloud elasticity and are started/stopped as appropriate when they are used.  Therefore, on first use the VM needs to be provisioned/started.
- For first time use, the VM needs to be configured with the Azure ML SDK & data science software
- The data set is copied (cached locally)
- The experiment scripts are generated and then deployed/executed on the compute VM
- During the experiment run, the experiment job is monitored actively to track logs/metrics
Note: Advanced options exist that allow the VM(s) to be always warm ready and reducing the prep time.

16. Click the **<- Back** button.  Notice (screenshot shown below) that the experiment is in the preparing state.  This will exist in this state for about 8-10 minutes.
<p align="center">
  <img width=800 height=439 src="https://github.com/bartczernicki/MachineLearning-AutomatedML-Titanic/blob/master/WalkthroughImages/AutomatedML-CreateExperimentPreparing.png">
</p>


17. When the experiment completes, it will be in the **Completed** state.  Click the link below the **RUN ID** column to go into the details of the experiment run.


### Task 2: Explore the finished experiment ###

1. Automated ML has completed the experiment with multiple models being built as well as a "final" model using an ensemble technique that combines multiple models into a single model enhancing perdictive power.  The created models and their associated performance metrics are shown in the grid below.  Notice that you can also download the best models as well as deploy them.  Click the **VotingEnsemble** link from the grid below.
<p align="center">
  <img width=800 height=353 src="https://github.com/bartczernicki/MachineLearning-AutomatedML-Titanic/blob/master/WalkthroughImages/AutomatedML-RunDetail.png">
</p>

2. In this dialog, you are taken to more advanced analysis, performance metrics & graphs.
<p align="center">
  <img width=800 height=378 src="https://github.com/bartczernicki/MachineLearning-AutomatedML-Titanic/blob/master/WalkthroughImages/AutomatedML-RunDetailModel.png">
</p>

