# Report: Predict Bike Sharing Demand with AutoGluon Solution
#### Mohamed Hassan

## Initial Training
### What did you realize when you tried to submit your predictions? What changes were needed to the output of the predictor to submit your results?
Predctions were all above zeros so I did not need to change anything.

### What was the top ranked model that performed?
The top randed Model was `WeightedEnsemble_L2`. And This is expected as ensamble methods peform usually better. And While XGBoost is an ensamble method but without extensive tuning its performance was mediocare.

## Exploratory data analysis and feature creation
### What did the exploratory analysis find and how did you add additional features?
The time serise is periodic and there is seasonality that depends on weekday, hour and day of the year so I add those features. 

### How much better did your model preform after adding additional features and why do you think that is?
The model performed 250% better because it can easily adapt to the seasonal change acrross the week and day.
## Hyper parameter tuning
### How much better did your model preform after trying different hyper parameters?
The boost in performance was around 40% higher.
### If you were given more time with this dataset, where do you think you would spend more time?
I will spend most of it exploring features and dependencies between the counts and input features and between features and each others.

### Create a table with the models you ran, the hyperparameters modified, and the kaggle score.

| model         | hpo1                          | hpo2                          | hpo3                  | score   |
|---------------|-------------------------------|-------------------------------|-----------------------|---------|
| initial       | default                       | default                       | default               | 1.86413 |
| add_features  | default                       | default                       | default               | 0.71615 |
| hpo           | GBM: num_boost_round: 100     | CAT: iterations: 100          | default               | 0.51796 |
| hpo           | default                       | default                       | multimodel:True        | 0.49363 |

### Create a line plot showing the top model score for the three (or more) training runs during the project.


![model_train_score.png](img/model_train_score.png)

### Create a line plot showing the top kaggle score for the three (or more) prediction submissions during the project.

TODO: Replace the image below with your own.

![model_test_score.png](img/model_test_score.png)

## Summary

All in all, Autogluan performs really well as an automl. However that comes at a cost of a high compution because it simply really in bruteforce to find best models. However, It is very useful to use it as a baseline selector. Then by means of feature engineering and expert insights we can fine tune best models to achieve optimal performace.
