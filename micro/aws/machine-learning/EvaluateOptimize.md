# Evaluate and Optimize

### Evaluation Steps
* __Define Evaluation__ : Decide what metric or metrics we should use to decide if the algorithm is _good enough_.
* __Evaluate__ : Review the metrics during or after the training process. This might be manual or automatic depending on the algorithm.
* __Tune__ : Adjust huper parameters, data, the evaluation strategy or even the entire algorithm to bring us close ot the desired results.
* __Validation__
  * Online Validation :  Validation under real-world conditions. eg., Canary deployment (route 1% traffic to see the how new model works) nor A/B Testing
  * Offline Validation : Validation done using test set of data. eg., K-fold validation and black testing with historical data

* Alorithm Metrics - Cloud Watch integrates well with sagemaker for both logging and metric charting and dashboarding.
  * Training Metrics
  * Validation Metrics

* Underfitting - Our model just is not very reflective of the underlying data shape. Maybe we need some more variables to help train our model and achieve a better fit. Positive residual means underfitting.
* Overfitting - Our model is too dependent on that specific data that we used to train. If it sees any new data, accuracy will likely be poor unless the data is identical to the training data. We have trained our algorithm to memorize rather than generalize. Negative residual means overfitting.
* Robust Model : Our model fits the training data but also does reasonably well on new data which it has never seen. It can _deal_ with noise in a data. It can generalize effectively for that new data.
* Prevent Overfitting
  * More data - sometimes more data will provide enough additional entropy to steer your aglorithm away from overfitting.
  * Early stopping - Terminiate the training process before it has a chance to _overtrain_. Many algorithms include this option as a hyper paramater.
  * Sprinkle in some noise - Your training data could be TOO clean and you might need to inctroduce some noise to generalize the model
  * Regulate - Regularization forces your model to be more general by creating constraints around weights or smoothing the input data.
  * Ensembles - Combine different models together to either amplify individual weaker models (boosting) or smooth out strong models (baggin)
  * Ditch some features - (Aka Feature selection)  Too many irrelevant features can influence the model in a negative way by drowning out the signal with noise.

* Regression Accuracy: I'm predicting a number 45 but the actual is 42 so the residual is `42-45=-3` 
  * Root Mean Square Error (RMSE) : A measure of the distance betwen an actual observation and predicted value. Lower the RMSE is better RMSE = sqrt(1/n Sum(actual-predicter)^2)
* F1 Score
  * Recall = (we guessed right)/(we guessed right + we should have flagged these too)
  * Precision = (We guessed right)/(We guessed right  + we flagged these but we were wrong)

* Improving model accuracy
  * Collect Data : Increase the number of training examples available to the model. More good data usually means a more accurate model.
  * Feature processing : Provide additional quality variables or refine the existing variables so they are more representative.
  * Model parameter turning : Adjust the hyper parameters used by your training algorithm.
