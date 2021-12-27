# Module 12 Report Template

## Overview of the Analysis

In this section, describe the analysis you completed for the machine learning models used in this Challenge. This might include:

* Explain the purpose of the analysis.
* Explain what financial information the data was on, and what you needed to predict.
* Provide basic information about the variables you were trying to predict (e.g., `value_counts`).
* Describe the stages of the machine learning process you went through as part of this analysis.
* Briefly touch on any methods you used (e.g., `LogisticRegression`, or any resampling method).

The purpose of the analysis is to use a dataset of historical lending activity from a peer-to-peer lending services company to build a model that can identify the creditworthiness of borrowers. We are predicting which loans are healthy and which loans are high risk. According to our original dataset there were 75036 healthy loans and 2500 high risk loans using the value_counts function. The first stage was to split the data into testing and training datasets using train_test_split function. The next step is to instantiate and then fit the LogisticRegression model using training data. We then save the predictions on the testing data labels (y_pred) using the testing feature data (X_test) and the fitted LogisticRegression model. Finally evaluate the data using the balanced accuracy score, confusion matrix and classifcation report. 

Before modeling, in the instance of resampling, we would instantiate the random_oversampler model and then fit the original training data to the random_oversampler model so we are better able to predict the values of the minority dataset. We would then conduct LogisticRegression as before on the resampled training data. 

## Results

Using bulleted lists, describe the balanced accuracy scores and the precision and recall scores of all machine learning models.

* Machine Learning Model 1:
  * The accuracy is 95% which means that(TP+TN)/(TP+FP+TN+FN) = 0.95, indicating that the model identifies healthy and high risk loans approximately 95% of the time. 
  * The precision of the model for identifying a healthy loan is 1.00 which is the highest it can be, which indicates there are negligible false positives meaning almost all predicted healthy loans are actually healthy. This is great but it may indicate overfitting. The precision for identifying high risk loans is about 85%. 
  * The recall, meaning 99% of all healthy loans are predicted to be healthy (1% false negatives), while 91% of high risk loans are predicted to be high risk (9% are false negatives). 



* Machine Learning Model 2:
  * The accuracy in the oversampled model is 99.4% whereas the old model was 95%, so it went up by 4.4% and near 100% accuracy, meaning there were fewer false positives (high risk loan predicted as a healthy loan) and false negatives (healthy loans predicted as a high risk loan). 
  * The precision of healthy loans remained the same (1.00, because we only had 4 false positives) whereas the precision of high risk loans went down by 1%. 
  * The recall of healthy loans remains approximately the same at 99%, meaning 99% of healthy loans are predicted to be healthy (1% false negatives) and the recall of high risk loans increased from 91% to 99%.

## Summary

Summarize the results of the machine learning models, and include a recommendation on the model to use, if any. For example:
* Which one seems to perform best? How do you know it performs best?
* Does performance depend on the problem we are trying to solve? (For example, is it more important to predict the `1`'s, or predict the `0`'s? )

The machine learning model 2, which used resampled training data, is superior to machine learning model 1. We know it performs best using the accuracy score with is 99.4% versus model 1's 95% and the stronger recall for high risk loans at 99% versus model 1's 91%. Although model 2 had a 1% drop in precision regarding high risk loans, that means there were more false positives. However, false positives in this case mean that healthy loans were misclassified as high risk, which does not affect the firm's risk portfolio. False negatives are dangerous to a lender because high risk loans are being wrongly predicted as healthy. Therefore it is more important to predict the 1s (high risk loans) than the 0s (healthy loans) justifying model 2 as the better model due to the 8% increase in recall. 
