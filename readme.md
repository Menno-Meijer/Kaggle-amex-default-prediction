# American Express credit card default prediction Kaggle competition
### Competition information
In the [American Express default prediction competition](https://www.kaggle.com/competitions/amex-default-prediction) hosted on Kaggle.com it was the goal to apply machine learning to predict credit default.
Generate the most accurate models on an industrial scale data set that could challenge the current model used by American Express.
> Credit default prediction is central to managing risk in a consumer lending business. Credit default prediction allows lenders to optimize lending decisions, which leads to a better customer experience and sound business economics. Current models exist to help manage risk. But it's possible to create better models that can outperform those currently in use.

*(Quote from the competition page)*

### Models used for submission
My final submission for the Kaggle competition was an ensemble of two LightGBM models with DART boosting,
an artificial neural network (ANN) and a XGBoost model. 
The weights of the ensemble between these models were determined by highest possible evaluation metric (specific competition metric) based on the out of fold predictions (OOF). 
The models in the ensemble were created based on three data sets (V23, V29 and V32), see the table below.
The data preparation for data version 32 is the same as for version 29,
the only difference is that in V32 the NaN values are initially filled in with -127. After feature engineering and data processing the -127 values are ultimately replaced by NaN again.
Whereas data preparation for data version 23 consists of fewer features. 
This data set was used for the XGBoost model in the ensemble, as the XGBoost model was unable to train on larger data sets due to memory size.

| Model | Data preparation | Percentage in ensemble |
| ------------- | ------------- | ------------- |
| LightGBM DART V3 | Version 29  | 20% |
| LightGBM DART V4 | Version 32  | 32.5% |
| XGBoost V10 | Version 23  | 32.5% | 
| Artificial NN | Version 29  | 15% |

### Competition result
My final leaderboard place was number 1744 out of 4874 (top 36%), with a score of 0.80658.
I choose my final submission based on my internal OOF scores and not on for instance Public Score of each submission.

Reflecting back on my submissions, my final submission was not my best scoring ensemble. 
The ensemble that provided the best possible leaderboard score would have been a combination of LightGBM DART V3, LightGBM DART V4 and XGBoost V10.
This ensemble scored 0.80704, which would be place 678 (top 14%).
However, because this combination of models gave a lower OOF score it was not chosen as final submission. 
Which could possibly be explained by overfitting of the models on the train data and/or public test data, and the added noise to the original data.