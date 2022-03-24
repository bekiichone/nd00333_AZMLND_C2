# Azure MLE Project 2: Operationilizing Machine Learning

In this project I have deployed model and pipeline and made possible to send API requests with JSON payloads. The deployed model was the best model chosen by Auto ML run. Overall, I have learned the model deployment and documentation process as well as how to deploy pipeline. Challenging part was to comprehend the step by step process of deploying a pipeline, since it consists of a handful of steps and libraries. 

## Architectural Diagram
!['Proof'](https://github.com/bekiichone/nd00333_AZMLND_C2/blob/master/sample_screenshots/project%202%20architecture.jpg)
Model and Pipeline deployment processes consist of essentially similar steps, yet there are subtle differences. Before any experimetns we have to create Compute Cluster and Compute Instance for notebooks and experiments to be able to run. 

For Model deployment, we upload dataset to Workspace and create AutoML Run (experiment will be created automatically). After AutoML is finished, we deploy the best model of AutoML. After deployment is finished we can consume the endpoint by sending http requests onto REST url. 

For Pipeline deployment, we first create an experiment in existing Workspace. Then attach an already created cluster to it, so that we can run pipeline. In the notebook, we load the dataset and configure the AutoML run. Next we create an AutoMLStep where we pass AutoMLConfig. Then we create a pipeline consisting of Steps we created before. Then we submit created Pipeline to the Experiment. After Training is finihsed we can publish it to the workspace. Finally, we have to retrieve auth_header in order to access the endpoint for consumption. 

## Key Steps
*TODO*: Write a short discription of the key steps. Remeber to include all the screenshots required to demonstrate key steps. 

## Screen Recording
https://www.youtube.com/watch?v=DD4tE6SZjnw

## Standout Suggestions
*TODO (Optional):* This is where you can provide information about any standout suggestions that you have attempted.
