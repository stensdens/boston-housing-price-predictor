# Overview

This simple flask application can be used to predict the boston housing prices.


## Project Plan


This is the [Trello Board](https://trello.com/b/47mH7lOy/boston-house-prices) tracking the tasks for the project.
* A link to a spreadsheet that includes the original and final project plan>

## Instructions

<TODO:  
* Architectural Diagram (Shows how key parts of the system work)>

<TODO:  Instructions for running the Python project.  How could a user with no context run this project without asking you for any help.  Include screenshots with explicit steps to create that work. Be sure to at least include the following screenshots:

* Project running on Azure App Service

* Project cloned into Azure Cloud Shell

![Cloned project](D:\workspace\boston-housing-price-predictor\screenshots\1_Setup-Cloud-Shell_Git_Clone.png)

* Passing tests that are displayed after running the `make all` command from the `Makefile`

* Output of a test run
  ![Run Part 1](D:\workspace\boston-housing-price-predictor\screenshots\3_Part1_Local_Test.png)
  ![Run Part 2](D:\workspace\boston-housing-price-predictor\screenshots\3_Part2_Local_Test.png)

* Successful deploy of the project in Azure Pipelines.  [Note the official documentation should be referred to and double checked as you setup CI/CD](https://docs.microsoft.com/en-us/azure/devops/pipelines/ecosystems/python-webapp?view=azure-devops).

* Running Azure App Service from Azure Pipelines automatic deployment

* Successful prediction from deployed flask app in Azure Cloud Shell.  [Use this file as a template for the deployed prediction](https://github.com/udacity/nd082-Azure-Cloud-DevOps-Starter-Code/blob/master/C2-AgileDevelopmentwithAzure/project/starter_files/flask-sklearn/make_predict_azure_app.sh).
The output should look similar to this:

```bash
udacity@Azure:~$ ./make_predict_azure_app.sh
Port: 443
{"prediction":[20.35373177134412]}
```

* Output of streamed log files from deployed application

> 

## Enhancements

<TODO: A short description of how to improve the project in the future>

## Demo 

<TODO: Add link Screencast on YouTube>


