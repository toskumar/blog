# Machine Learning FAQ

* __Regularization__  is a machine learning technique that you can use to obtain higher-quality models. 

* __Number of Passes__ The number of times that you let Amazon ML use the same data records is called the number of passes.

* __AUC__ Area Under the ROC Curve (AUC) measures the ability of a binary ML model to predict a higher score for positive examples as compared to negative examples.

* __Macro-averaged F1-score__ The macro-averaged F1-score is used to evaluate the predictive performance of multiclass ML models.

* __RMSE__ 	The Root Mean Square Error (RMSE) is a metric used to evaluate the predictive performance of regression ML models.

* __Cut-Off__ Conversion of a numeric prediction score into a 0 or 1 label 

* __Confusion Matrix__
  |Actual/Predicted | Predicted True | Predicted False | |
  | --- | --- | --- | 
  | Actual True | I predicted correctly! (True Positive)     | I was wrong (False Positive) (Type I error) | Precision = TP/(TP+FP) |
  | Actual False| I was wrong. (False Negative) (Type II error) | I predicted Correctly! (True Negative)| Accuracy = (TP + TN)/(TP+FP+FN+TN)|
  | |Recall = TP/(TP+FN) | FPR=FP/(FP/TN) |

* __Accuracy__ measures the percentage of correct predictions. Accuracy = (TP + TN)/(TP+FP+FN+TN)

* __Precision__ Precision shows the percentage of actual positive instance. Precision = TP/(TP+FP)

* __Recall__ Recall shows the percentage of actual positives among the total number of relevant instances. Recall = TP/(TP+FN)

* __False Positive Rate__ measures the false alarm rate or the fraction of actual negatives that are predicted as positive. FPR = FP/(FP+TN) 
