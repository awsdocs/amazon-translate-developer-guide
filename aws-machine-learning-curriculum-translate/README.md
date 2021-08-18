# Introduction to the Course


## Amazon Web Services (AWS)

AWS is a cloud computing platform where businesses access technologies to easily solve their technical problems. AWS hosts over 200 services, ranging from servers, storage, mobile development, and security. AWS provides a large set of machine learning services that can be used even by those without prior experience. 

## Overview

This GitHub Repository contains Jupyter notebooks that demonstrate how to use AWS Machine Learning Services to solve business problems in natural language processing. Through the next series of modules, these modules will introduce the basics of machine learning (ML) so you can become ML literate. Users will follow step-by-step tutorials about how to use AWS Products to solve real-world problems. 


## Background 

These notebooks are intended for individuals working in technical roles who want to use AWS services for their business. Prior background in Python and Jupyter Notebooks is assumed. No mathematical or statistical background is required. 

The notebooks can be opened through [Amazon SageMaker](https://aws.amazon.com/sagemaker/). Amazon SageMaker is a fully managed service for machine learning workflows. They can be opened using [JupyterLab](https://jupyterlab.readthedocs.io/en/stable/getting_started/overview.html#:~:text=JupyterLab%20is%20a%20next%2Dgeneration,%2C%20integrated%2C%20and%20extensible%20manner.). JupyterLab lets you work with Jupyter Notebooks and other files in an integrated web-based user interface.

## Before You Begin 

In order to run the modules in the curriculum, you will need to set up your AWS account. An AWS Account is how you create and manage your AWS Resources. For more information on how to create an AWS Account, see [here](https://aws.amazon.com/premiumsupport/knowledge-center/create-and-activate-aws-account/). 

For each module, you will need to set up an IAM role. An IAM role is a role you create in your AWS account that has specific permissions to access AWS resources. Learn more about how to set up IAM roles [this guide to IAM](https://docs.aws.amazon.com/sagemaker/latest/dg/security-iam.html).

## How to Open the Curriculum 

After you have all the accounts set up, you can open the Jupyter notebooks that contain the curriculum. You will open them in Amazon SageMaker. Amazon SageMaker Notebook Instance is an instance that launches the Jupyter Notebook App in the browser. Learn more about Amazon SageMaker Notebook Instances [this guide to get started](https://docs.aws.amazon.com/sagemaker/latest/dg/gs-setup-working-env.html).

1. Log into AWS account. 
2. Go to the Amazon SageMaker Console.
3. Find Notebook on the left navigation bar. Choose *Notebook instances*. 
4. Choose _Create notebook instance_. 
5. Fill in notebook instance settings. Input a unique name under _notebook instance name._ Leave other options as the default. 
6. Under *Permissions and encryption*, open the drop down menu and choose *Create a new role.* Keep the default settings. Keep the other settings in this section as the default. 

<img width="569" alt="Screen Shot 2021-08-17 at 3 13 58 PM" src="https://user-images.githubusercontent.com/88006687/129786612-b56a718c-f96e-4da9-970c-84be795b83f9.png">

7. Under the *Git repositories*, open the drop down menu and choose _Clone a public Git repository to this notebook instance only_. Copy the URL of this GitHub repository: https://github.com/awszhouanni/aws-machine-learning-curriculum-translate. Paste it under _Git repository URL_.

<img width="475" alt="Screen Shot 2021-08-17 at 3 19 24 PM" src="https://user-images.githubusercontent.com/88006687/129787279-16bc2302-59dc-4358-9745-0ff0dea6af12.png">

8. Choose _Create notebook Instance_. 
9. SageMaker takes a few minutes to create the notebook instance. Under _Notebook instances_, find your unique notebook instance. Wait for the status to change from _Pending_ to _InService_. You can refresh the page.  

<img width="897" alt="Amazon SageMaker Console GitHub Repositories" src="https://user-images.githubusercontent.com/36568498/126387067-5a4e3ad2-8b19-4097-9e54-f44128ef4c47.png">


Now, you can access the repostories through Amazon SageMaker's notebook instances. 
1. Choose the notebook instance titled *Module #1*. 
2. Choose *Open JupyterLab.* 
3. Then, choose the folder "Module 1." 
4. Choose the JupyterNotebook titled "Translate text into spoken translations with Amazon Translate and Amazon Polly" to begin the curriculum.
