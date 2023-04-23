# Overview

This simple flask application can be used to predict the boston housing prices.


## Project Plan


This is the [Trello Board](https://trello.com/b/47mH7lOy/boston-house-prices) tracking the tasks for the project.

The spreadsheet can be found under [Project Plan](project-management.xlsx)

## Instructions

Architectural Overview
![Architecture Diagram](architecture.png "Architecture Diagram")

<TODO:  Instructions for running the Python project.  How could a user with no context run this project without asking you for any help.  Include screenshots with explicit steps to create that work. Be sure to at least include the following screenshots:

* Project running on Azure App Service

* Project cloned into Azure Cloud Shell

![](screenshots/1_Setup-Cloud-Shell_Git_Clone.png)

* Passing tests that are displayed after running the `make all` command from the `Makefile`

* Output of a test run

![](screenshots/3_Part1_Local_Test.png)
![](screenshots/3_Part2_Local_Test.png)

* Successful deploy of the project in Azure Pipelines.  

![](screenshots/5_azure_cli_to_deploy.png))

* Running Azure App Service from Azure Pipelines automatic deployment
![6_successful_deploy_via_pipeline.png](screenshots/6_successful_deploy_via_pipeline.png)

* Successful prediction from deployed flask app in Azure Cloud Shell. 

```bash
(.env) odl_user [ ~/boston-housing-price-predictor ]$ ./make_predict_azure_app.sh 
Port: 443
{"prediction":[2.431574790057212]}
(.env) odl_user [ ~/boston-housing-price-predictor ]$ 
```
![7_successful_prediction.png](screenshots%2F7_successful_prediction.png)

* Output of streamed log files from deployed application

> 2023-04-23T20:55:23.401153905Z 169.254.129.1 - - [23/Apr/2023:20:55:23 +0000] "POST /predict HTTP/1.1" 200 35 "-" "curl/7.88.1"
2023-04-23T20:55:30.295450099Z /tmp/8db443cb09a13c5/antenv/lib/python3.10/site-packages/sklearn/base.py:329: UserWarning: Trying to unpickle estimator LinearRegression from version 1.1.3 when using version 1.0.2. This might lead to breaking code or invalid results. Use at your own risk. For more info please refer to:
2023-04-23T20:55:30.295490003Z https://scikit-learn.org/stable/modules/model_persistence.html#security-maintainability-limitations
2023-04-23T20:55:30.295497203Z   warnings.warn(
2023-04-23T20:55:30.297392567Z [2023-04-23 20:55:30,295] INFO in app: JSON payload: %s json_payload
2023-04-23T20:55:30.298551466Z [2023-04-23 20:55:30,298] INFO in app: inference payload DataFrame: %s inference_payload
2023-04-23T20:55:30.301040381Z [2023-04-23 20:55:30,300] INFO in app: Scaling Payload: %s payload
2023-04-23T20:55:30.306648464Z [2023-04-23 20:55:30,306] INFO in app: Predicted value is: [2.431574790057212]
2023-04-23T20:55:30.309914446Z 169.254.129.1 - - [23/Apr/2023:20:55:30 +0000] "POST /predict HTTP/1.1" 200 35 "-" "curl/7.88.1"

## Enhancements

- it should be possible to select the library which is used in the prediction
- better error codes


## Demo 

<TODO: Add link Screencast on YouTube>


