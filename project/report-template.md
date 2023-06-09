# Report: Predict Bike Sharing Demand with AutoGluon Solution
#### JOAN GERARD

## Initial Training
### What did you realize when you tried to submit your predictions? What changes were needed to the output of the predictor to submit your results?
Negative predictions are not valid and the submission may be rejected due to this. We need to set this predictions to be 0 before submitting. 

### What was the top ranked model that performed?
The one that worked bettter with kaggle predictions was the one we tunned which gave us a public score of 1.22 but it did not perform well with our training set giving us a score of 139. However, the one that worked better with our training set was the add_features one.

## Exploratory data analysis and feature creation
### What did the exploratory analysis find and how did you add additional features?
It shows how many features we have, what the types of each feature is and what the data distribution for all the features is. We discovered that the type of seasonal and weather features was int and we changed it to be categorical for both the train and test datasets. The hour, weekday and month features were added into the dataset.

### How much better did your model preform after adding additional features and why do you think that is?
It did not performed much better with the submission dataset, probably because 10 minutes run was not enough for autogluon to test enough models.  

## Hyper parameter tuning
### How much better did your model preform after trying different hyper parameters?
The model performed much better with the submission dataset reporting a score of 1.20

### If you were given more time with this dataset, where do you think you would spend more time?
I would like to perform more feature engineering: see what is the correlation between different features together with the target, also try to see feature importance and trying to filter the less important features out. Also I would like to explore more models, more parameters, etc...

### Create a table with the models you ran, the hyperparameters modified, and the kaggle score.
|model|hpo1|hpo2|hpo3|score|
|--|--|--|--|--|
|initial|50.5|51.6|53.2|1.81|
|add_features|50.5|51.6|53.0|1.80|
|hpo|139.2|139.7|139.8|1.22|

### Create a line plot showing the top model score for the three (or more) training runs during the project.

![model_train_score.png](model_train_score.png)

### Create a line plot showing the top kaggle score for the three (or more) prediction submissions during the project.


![model_test_score.png](model_train_score_kaggle.png)

## Summary
It is important to do a correct exploration of the data in order to have a good understanding of it. When we spend more time trying to figure out the relation between the features and the target, we have more chances to find a better model.

Autogluon is a very complete tool that works as a blackbox to test many models with different parameters. The more time we let autogluon execute, the more opportunities we have to find a better model.

Only artificial neural networks model was used for tunning of hyperparametters which clearly shows that is not a good fit for this dataset. This was because other models such as GBM were throwing some errors such as: `np.bool was deprecated`. Time was spent to try to fix this error with no success (probably, because the jupyter notebook was run locally and there were some dependencies issues). 
