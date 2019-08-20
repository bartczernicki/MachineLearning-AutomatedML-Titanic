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
