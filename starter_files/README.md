# Azure MLE Project 2: Operationilizing Machine Learning

In this project I have deployed model and pipeline and made possible to send API requests with JSON payloads. The deployed model was the best model chosen by Auto ML run. Overall, I have learned the model deployment and documentation process as well as how to deploy pipeline. Challenging part was to comprehend the step by step process of deploying a pipeline, since it consists of a handful of steps and libraries. 

## Architectural Diagram
!['Proof'](https://github.com/bekiichone/nd00333_AZMLND_C2/blob/master/sample_screenshots/project%202%20architecture.jpg)
Model and Pipeline deployment processes consist of essentially similar steps, yet there are subtle differences. Before any experimetns we have to create Compute Cluster and Compute Instance for notebooks and experiments to be able to run. 

For Model deployment, we upload dataset to Workspace and create AutoML Run (experiment will be created automatically). After AutoML is finished, we deploy the best model of AutoML. After deployment is finished we can consume the endpoint by sending http requests onto REST url. 

For Pipeline deployment, we first create an experiment in existing Workspace. Then attach an already created cluster to it, so that we can run pipeline. In the notebook, we load the dataset and configure the AutoML run. Next we create an AutoMLStep where we pass AutoMLConfig. Then we create a pipeline consisting of Steps we created before. Then we submit created Pipeline to the Experiment. After Training is finihsed we can publish it to the workspace. Finally, we have to retrieve auth_header in order to access the endpoint for consumption. 

## Key Steps

### Model Deployment
!['Proof'](https://github.com/bekiichone/nd00333_AZMLND_C2/blob/master/sample_screenshots/1%20BankMarketing%20Dataset.PNG)
  Initially we have to load dataset from provided link. Then we create an AutoML run upon the loaded dataset. 

!['Proof'](https://github.com/bekiichone/nd00333_AZMLND_C2/blob/master/sample_screenshots/2%20.PNG)
  Above figure shows the best model chosen by AutoML run. From my expertiment VotingEnsemble showed best performance.

!['Proof'](https://github.com/bekiichone/nd00333_AZMLND_C2/blob/master/sample_screenshots/3%20Experiment%20Completed.PNG)
  Above figure demonstrates the completed experiment created for AutoML run. 

!['Proof'](https://github.com/bekiichone/nd00333_AZMLND_C2/blob/master/sample_screenshots/4%20model%20deployed%20successfully.PNG)
  We take the best model and deploy it in the Workspace. Above picture shows the succesfully deployed model. 

!['Proof'](https://github.com/bekiichone/nd00333_AZMLND_C2/blob/master/sample_screenshots/5%20Applications%20Insight%20true.jpg)

Then we enable logging (Application Insights) via including service.update(enable_app_insights=True) code in logs.py as well as name of deployed web service. Above figure shows that Application Insights was enabled. Below is the output logs of log.py script. 
!['Proof'](https://github.com/bekiichone/nd00333_AZMLND_C2/blob/master/sample_screenshots/6%20logs%20py.PNG)


The next step was to create a documentation for deployed web service. By running swagger.sh script (we have to download swagger.json file from deployed model webpage beforehand) the docker container and Swagger UI were created. Then we have to run serve.py in a separate command line in order to create a documentation. Below figure demonstrates created documentation. 

!['Proof'](https://github.com/bekiichone/nd00333_AZMLND_C2/blob/master/sample_screenshots/7%20model%20deploy%20runs%20on%20localhost%202.PNG)

Finally, we can now send requests to deployed model and retrieve response. Below image shows the response after running endpoint.py script. 

!['Proof'](https://github.com/bekiichone/nd00333_AZMLND_C2/blob/master/sample_screenshots/8%20endpoint%20py%20result.png)

### Pipeline Deployment

The key step in pipeline deployment is constructing one. The pipeline constists of steps to run (in our case it was AutoMLStep). After the pipeline is submitted to experiment and completed, we can publish it. Below figures show the pipeline run and its endpoint. 

!['Proof'](https://github.com/bekiichone/nd00333_AZMLND_C2/blob/master/sample_screenshots/9%20ML%20studio%20scheduled%20run.PNG)
!['Proof'](https://github.com/bekiichone/nd00333_AZMLND_C2/blob/master/sample_screenshots/10%20pipeline%20endoint.png)

Here is how published pipeline looks. 

!['Proof'](https://github.com/bekiichone/nd00333_AZMLND_C2/blob/master/sample_screenshots/11%20pipeline%20created.PNG)
!['Proof'](https://github.com/bekiichone/nd00333_AZMLND_C2/blob/master/sample_screenshots/12%20pipeline%20endoint%20published.png)

At this point we can consume the pipeline and run the pipepline via http requests. 

In the notebook sometimes it might be crucial to track the pipeline run progress. Fortunately, there is a RunDetails Widget. Below figure demonstrates the progress of the pipeline run in this project. 

!['Proof'](https://github.com/bekiichone/nd00333_AZMLND_C2/blob/master/sample_screenshots/13%20RunDetails%20Widget.png) 

## Future Improvements

For now our pipeline consists of only 2 modules. As a potential improvement could be an addition of feature engineering step. Definately there should be some exploratory data analysis done prior to any modelling since it might bring some valuable insights about data. Lastly, I assume dataset is clean, but in reality datasets are rarely clean, so a data cleaning step should added. 

## Screen Recording
https://www.youtube.com/watch?v=DD4tE6SZjnw

## Standout Suggestions
*TODO (Optional):* This is where you can provide information about any standout suggestions that you have attempted.
