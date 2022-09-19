# American Express credit card default prediction Kaggle competition

My final submission for the Kaggle competition was an ensemble of two LightGBM models with DART boosting,
an artificial neural network (ANN) and a XGBoost model. 
The weights of the ensemble between these models were determined by highest possible evaluation metric (specific competition metric) based on the out of fold predictions (OOF). 
The models in the ensemble were created based on two data sets (V29 and V32).
The data preperation for data version 32 is the same as for version 29,
the only difference is that in V32 the NaN values are initially filled in with -127. After feature engineering and data processing the -127 values are ultimately replaced by NaN again. 
