# Optimizing an ML Pipeline in Azure

## Overview
This project is part of the Udacity Azure ML Nanodegree.
In this project, we build and optimize an Azure ML pipeline using the Python SDK and a provided Scikit-learn model.
This model is then compared to an Azure AutoML run.

## Summary
The bank marketing's dataset contains 21 columns and 3300 rows. The data contains information on how many times a client was contacted during the campaign, job, loan, housing, and contact history on whether the client opted for a fixed loan rate deposit. The best performing model was VotingEnsemble with the accuracy of 0.9171 using AutoML. 

## Scikit-learn Pipeline
First, we created a worskpace and curated environment to initialize the compute cluster. Then, the dataset is tabular so it was imported using an URL in the train.py script and the data was split into training and test datasets. Next, the logistic regresion was the algorithm used to obtain the best run and it was used for training of the hyperparameter tunning C and max_iter. The banditPolicy was used for early termintion of the hyperdrive run so once it is done running, it save the respurced needed for evaluation. Once the best model was determined based on the hyperparameter, the model was saved.

**What are the benefits of the parameter sampler you chose?**
I utilized the random sampling because each sample has a change of being selected, in this case, it runs through all the different samples and selects the best one.

**What are the benefits of the early stopping policy you chose?**
The banditPolicy is an early termination policy based on slack criteria. Bandit terminates runs where the primary metric is not within the specified slack factor/slack amount compared to the best performing run.

## AutoML
**In 1-2 sentences, describe the model and hyperparameters generated by AutoML.**
AutoML runs our training model and provides the best possible model out of all of them. For this example, voting ensemble provided an accuracy of 91.71%. This model predicts the output based on small models, the number of cross validation for this case is 4. We also selected inside the automl_config, the type of algorithm used which classification, training data, primary metric, compute target, label column which is what we are trying to predict. 

## Pipeline comparison
**Compare the two models and their performance. What are the differences in accuracy? In architecture? If there was a difference, why do you think there was one?**
In the hyperdrive, we obtained an accuracy of 91.59% compared to autoML voting ensemble which is 91.71%. The autoMl took about 30 minutes to run 23 models whereas hyperdrive model was around 10 minutes to run 10. AutoMl provided the option of running multiple models to selected the best one but it depends the type of dataset you are trying to run when it comes to select the best option. For this case, autoML provided a more in depth analysis in selected the best option.

## Future work
**What are some areas of improvement for future experiments? Why might these improvements help the model?**
I think concepts in Machine learning like feature engineering could be a integrated with this experiment for better data optimization. Also, we are using a classification technique but we can try to experiment others like AUC.


## Proof of cluster clean up
**If you did not delete your compute cluster in the code, please complete this section. Otherwise, delete this section.**
**Image of cluster marked for deletion**

![Alt deletecompute](deleteinstancecompute.png)
