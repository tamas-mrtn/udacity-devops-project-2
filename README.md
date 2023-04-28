# Overview

[![CI](https://github.com/tamas-mrtn/udacity-devops-project-2/actions/workflows/pythonapp.yml/badge.svg)](https://github.com/tamas-mrtn/udacity-devops-project-2/actions/workflows/pythonapp.yml)
[![CD](https://dev.azure.com/udacity-devops/my-test-project/_apis/build/status%2Ftamas-mrtn.udacity-devops-project-2?branchName=main)](https://dev.azure.com/udacity-devops/my-test-project/_build/latest?definitionId=3&branchName=main)

This project showcases how to build a simple CI/CD pipeline using Github Actions and Azure DevOps. We deploy a simple flask-based API to make house price predictions. We use Makefile to setup the Continuous Integration on Github Actions. Then, we integrate the project with Azure Pipelines to enable Continuous Delivery that adds the committed changes to Azure App Services.

## Project Plan

* [Trello board of the project](https://trello.com/invite/b/GU6Nhn6s/ATTIb637823876c8106c5817a5c6cc3a735eF2E5CECA/project-management)
* Project plan: please find project-management.xlsx

## Instructions

### Prerequisities

Before embarking on this project please make sure you have the following:

* An Azure account: https://portal.azure.com/
* A Github account: https://github.com/
* An Azure DevOps account: https://dev.azure.com/)

### CI architecture

The below image showcases how the different components work together to create the continuous integration flow. In essence, whenever a git push or pull request arrives to the main branch on the git repo (ie. initiated from Azure Cloud Shell), Github Actions will run an Actions Container that executes the commands set in the Actions Config file, which in this case is to execute the steps in the Makefile.

![CI architecture](ci-diagram.png)

### CD architecture

The below image shows what happens after a successful CI run on Github Actions. Github sends a message to Azure Pipelines which then will run the config that will deploy the changes to Azure App Service.

![CD architecture](cd-diagram.png)


### How to start

Please follow these steps in order to setup this Python project:

* In Azure Portal, request a Cloud shell and clone this repo: ![Cloned repo](cloud-shell.png)
* Run `make setup` command in Cloud shell to create virtual environment
* Run `source ~/.udacity-devops/bin/activate` to activate virtual env
* Run `make all` to install dependencies, run linter and run tests ![Passed tests](tests.png)
* Verify CI process by adding a commit and checking Github Actions UI if the process passed the tests: ![Actions](actions.png)
* Authorize Azure App Service and try manually deploying the app: `az webapp up -n <your-appservice>`
* Verify that your app has been deployed: `https://<your-appservice>.azurewebsites.net/`
* Run load test with locust: `locust -f locustfile.py` ![Locust](locust.png)
* Follow the official documentation to deploy your app in Azure Pipelines: [Documentation](https://learn.microsoft.com/en-us/azure/devops/pipelines/ecosystems/python-webapp?view=azure-devops)



<TODO:  Instructions for running the Python project.  How could a user with no context run this project without asking you for any help.  Include screenshots with explicit steps to create that work. Be sure to at least include the following screenshots:

* Project running on Azure App Service

* Project cloned into Azure Cloud Shell

* Passing tests that are displayed after running the `make all` command from the `Makefile`

* Output of a test run

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


