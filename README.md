![example workflow](https://github.com/stensdens/boston-housing-price-predictor/actions/workflows/main.yml/badge.svg)


# Overview

This simple flask application can be used to predict the boston housing prices.


## Project Plan


This is the [Trello Board](https://trello.com/b/47mH7lOy/boston-house-prices) tracking the tasks for the project.

The spreadsheet can be found under [Project Plan](project-management.xlsx)

## Instructions

Architectural Overview
![Architecture Diagram](architecture.png "Architecture Diagram")


* Project running on Azure App Service

Login into azure and open your Azure Cloud Shell

Create a ssh key and add it to your github account

Then clone the project

build it by executing make all

then you can run it via python app.py

you can perform a prediction by executing the script make_prediction.sh



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


* Run performance test via locus


![8_locus_run.png](screenshots%2F8_locus_run.png)

````bash
sdrag@DESKTOP-KH8BSO9 MINGW64 /d/workspace/boston-housing-price-predictor
$ locust --headless --users 1 --spawn-rate 10 -H https://bostonhousepricepredictor.azurewebsites.net/
[2023-04-23 23:51:18,039] DESKTOP-KH8BSO9/INFO/locust.main: No run time limit set, use CTRL+C to interrupt
[2023-04-23 23:51:18,040] DESKTOP-KH8BSO9/INFO/locust.main: Starting Locust 2.15.1                                                                              
Type     Name                                                                          # reqs      # fails |    Avg     Min     Max    Med |   req/s  failures/s
--------|----------------------------------------------------------------------------|-------|-------------|-------|-------|-------|-------|--------|-----------
--------|----------------------------------------------------------------------------|-------|-------------|-------|-------|-------|-------|--------|-----------
         Aggregated                                                                         0     0(0.00%) |      0       0       0      0 |    0.00        0.00
                                                                                                                                                                
[2023-04-23 23:51:18,041] DESKTOP-KH8BSO9/INFO/locust.runners: Ramping to 1 users at a rate of 10.00 per second                                                 
[2023-04-23 23:51:18,041] DESKTOP-KH8BSO9/INFO/locust.runners: All users spawned: {"QuickstartUser": 1} (1 total users)                                         
Type     Name                                                                          # reqs      # fails |    Avg     Min     Max    Med |   req/s  failures/s
--------|----------------------------------------------------------------------------|-------|-------------|-------|-------|-------|-------|--------|-----------
POST     //predict                                                                          1     0(0.00%) |    488     488     488    488 |    0.00        0.00
--------|----------------------------------------------------------------------------|-------|-------------|-------|-------|-------|-------|--------|-----------
         Aggregated                                                                         1     0(0.00%) |    488     488     488    488 |    0.00        0.00

Type     Name                                                                          # reqs      # fails |    Avg     Min     Max    Med |   req/s  failures/s
--------|----------------------------------------------------------------------------|-------|-------------|-------|-------|-------|-------|--------|-----------
POST     //predict                                                                          1     0(0.00%) |    488     488     488    488 |    0.00        0.00
--------|----------------------------------------------------------------------------|-------|-------------|-------|-------|-------|-------|--------|-----------
         Aggregated                                                                         1     0(0.00%) |    488     488     488    488 |    0.00        0.00

Type     Name                                                                          # reqs      # fails |    Avg     Min     Max    Med |   req/s  failures/s
--------|----------------------------------------------------------------------------|-------|-------------|-------|-------|-------|-------|--------|-----------
POST     //predict                                                                          2     0(0.00%) |    303     118     488    120 |    0.33        0.00
--------|----------------------------------------------------------------------------|-------|-------------|-------|-------|-------|-------|--------|-----------
         Aggregated                                                                         2     0(0.00%) |    303     118     488    120 |    0.33        0.00

         Aggregated                                                                         2     0(0.00%) |    303     118     488    120 |    0.33        0.00

Type     Name                                                                          # reqs      # fails |    Avg     Min     Max    Med |   req/s  failures/s
Type     Name                                                                          # reqs      # fails |    Avg     Min     Max    Med |   req/s  failures/s
--------|----------------------------------------------------------------------------|-------|-------------|-------|-------|-------|-------|--------|-----------
POST     //predict                                                                          2     0(0.00%) |    303     118     488    120 |    0.33        0.00
--------|----------------------------------------------------------------------------|-------|-------------|-------|-------|-------|-------|--------|-----------
POST     //predict                                                                          2     0(0.00%) |    303     118     488    120 |    0.33        0.00
--------|----------------------------------------------------------------------------|-------|-------------|-------|-------|-------|-------|--------|-----------
         Aggregated                                                                         2     0(0.00%) |    303     118     488    120 |    0.33        0.00

Type     Name                                                                          # reqs      # fails |    Avg     Min     Max    Med |   req/s  failures/s
--------|----------------------------------------------------------------------------|-------|-------------|-------|-------|-------|-------|--------|-----------
POST     //predict                                                                          3     0(0.00%) |    244     118     488    130 |    0.25        0.00
--------|----------------------------------------------------------------------------|-------|-------------|-------|-------|-------|-------|--------|-----------
         Aggregated                                                                         3     0(0.00%) |    244     118     488    130 |    0.30        0.00

Response time percentiles (approximated)
Type     Name                                                                                  50%    66%    75%    80%    90%    95%    98%    99%  99.9% 99.99%   100% # reqs
--------|--------------------------------------------------------------------------------|--------|------|------|------|------|------|------|------|------|------|------|------
POST     //predict                                                                             130    130    490    490    490    490    490    490    490    490    490      3
--------|--------------------------------------------------------------------------------|--------|------|------|------|------|------|------|------|------|------|------|------
         Aggregated                                                                            130    130    490    490    490    490    490    490    490    490    490      3

()

````

## Enhancements

- it should be possible to select the library which is used in the prediction
- better error codes


## Demo 

[See the demo here](https://youtu.be/d3Agl9_dXhk)


