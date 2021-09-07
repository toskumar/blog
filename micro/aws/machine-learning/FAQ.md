# Machine Learning FAQ

* __Regression__ model is to predict a numerical value
* __Multiclass__ model is to predict a pre-defined set of values
* __Binary__ model is to predict one of the two states, such as true or false 

* __Batch Prediction__ a set of observations that can run all at once
* __Real-time Prediction__ are for applications with a low latency requirement, such as interactive web, mobile, or desktop applications.

* __Machine Learning Situations__ when you can't code the rules and you can't scale.

* __Feature Engineering__ 
  * __Replace missing data__ is knows as imputation. Common strategy is to replace missing data with mean or median value. It is important to understand your data before choosing a strategy for replacing missing values.
  * __Forming Cartesian products__ of one variable with another variable eg., variable A, B, C with Z => A_Z, B_Z and C_Z 
  * __Binning__ numeric variables to categories eg., the continuous numeric feature age is not linearly correlated with the likelihood to purchase a book
  * __Domain-specific__ features eg., l, b, h and introduce v=l*b*h
  * __Variable-specific__ a sentence has generic ways of processing. eg., forming n-grams from text “the fox jumped over the fence”
 
* __Learning Algorithm__ The learning algorithm’s task is to learn the weights for the model. It consists of a loss function and an optimization technique (to reduce the loss). The optimization technique used in Amazon ML is online Stochastic Gradient Descent (SGD).
  * For __binary classification__ , Amazon ML uses logistic regression (logistic loss function + SGD).
  * For __multiclass classification__ , Amazon ML uses multinomial logistic regression (multinomial logistic loss + SGD).
  * For __regression__ , Amazon ML uses linear regression (squared loss function + SGD).

* __Stochastic Gradient Descent__ is used to optimize many different type of machine learning algorithms including Linear Regression, Logistic Regression, Support Vector Machines etc.,

* __Hyperparameters__ are external parameters and can be set by user when initiating the algorithm and parameters are internal to the training model. Examples Learning rate, Epochs, Batch size.
  * __Learning Rate__ Determine the size of steps taken during gradient descent optimization. values are between 0 and 1
  * __Batch Size__ Number of samples used to train at any one time
  * __Epochs__ The number of times that the algorithm will process the entire training data 
  * __Number of Passes__ The number of times that you let Amazon ML use the same data records is called the number of passes.
  * __Shuffling/Randamoize__ your data results in better ML models
  * __Regularization__  is a machine learning technique that you can use to obtain higher-quality models. We apply regularization when the model is overfit. Regularization is achieved through regression. (A model is said to overfit when it performs well in training dataset and not in realworld)
    * L1 Regularization (Lassso Regression)
    * L2 Regularization (Ridge Regression)
  
* __Validation__ Data set can be divided into 70-80% training data and 30-20% testing data. In the 80% training data we can split the data into 6-10 equal parts for validating each part to get optimum result. This process is known as K-Fold Cross validation.

### Evaluate Model Accuracy
* __AUC__ Area Under the ROC Curve (AUC) measures the ability of a binary ML model to predict a higher score for positive examples as compared to negative examples.

* __Macro-averaged F1-score__ The macro-averaged F1-score is used to evaluate the predictive performance of multiclass ML models.

* __RMSE__ 	The Root Mean Square Error (RMSE) is a metric used to evaluate the predictive performance of regression ML models.

* __Cut-Off__ Conversion of a numeric prediction score into a 0 or 1 label 

* __Underfitting__ the training data when the model performs poorly on the training data.

* __Overfitting__ your training data when you see that the model performs well on the training data but does not perform well on the evaluation data.

* __Retraining Model__ It is a good practice to continuously monitor the incoming data and retrain your model on newer data if you find that the data distribution has deviated significantly from the original training data distribution. A simpler strategy is to train the model periodically, for example, daily, weekly, or monthly.

* __Confusion Matrix__

  |Actual/Predicted | Predicted True | Predicted False | |
  | --- | --- | --- | --- | 
  | __Actual True__ | I predicted correctly! (True Positive)     | I was wrong (False Positive) (Type I error) | Precision = TP/(TP+FP) |
  | __Actual False__ | I was wrong. (False Negative) (Type II error) | I predicted Correctly! (True Negative)| Accuracy = (TP + TN)/(TP+FP+FN+TN)|
  | |Recall = TP/(TP+FN) | FPR=FP/(FP/TN) |
  * __Accuracy__ measures the percentage of correct predictions. Accuracy = (TP + TN)/(TP+FP+FN+TN)
  * __Precision__ Precision shows the percentage of actual positive instance. Precision = TP/(TP+FP)
  * __Recall__ Recall shows the percentage of actual positives among the total number of relevant instances. Recall = TP/(TP+FN)
  * __False Positive Rate__ measures the false alarm rate or the fraction of actual negatives that are predicted as positive. FPR = FP/(FP+TN) 

* __TensorFlow__ is a ML Framework developed by __Google__ and __Keras__ is an opensource API interface for TersorFlow 

* __MXNet__ is a ML/DL Framework developed by __AWS and Microsoft__ and __Gluon__ is an opensource API interface for MXNet  

* __PyTorch__ is an opensource library used by Facebook AI research lab.

* __Scikit Learn__ is the most useful and robust library for machine learning in Python.

## AWS AI and ML Services

* __Amazon Lex__ is a service for building conversational interfaces into any application using voice and text.
* __Amazon Polly__ is a service that turns text into lifelike speech, allowing you to create applications that talk, and build entirely new categories of speech-enabled products. 
* __Amazon Translate__ is a neural machine translation service that delivers fast, high-quality, affordable, and customizable language translation. 
* __Amazon Textract__ is a machine learning service that automatically extracts text, handwriting and data from scanned documents that goes beyond simple optical character recognition (OCR) to identify, understand, and extract data from forms and tables.
* __Amazon Transcribe__ makes it easy for developers to add speech to text capabilities to their applications.
* __Amazon Forecast__ is a fully managed service that uses machine learning to deliver highly accurate forecasts.
* __Amazon Comprehend__ is a natural-language processing (NLP) service that uncover the meaning and relationships in text from customer support incidents, product reviews, social media feeds, news articles and documents.
* __Amazon Rekognition__ makes it easy to add image and video analysis to your applications.
* __Amazon Personalize__ is a fully managed machine learning service that goes beyond rigid static rule based recommendation systems.
* __Amazon Fraud Detector__ is a fully managed service that uses machine learning (ML) and more than 20 years of fraud detection expertise from Amazon, to identify potentially fraudulent activity.
* __Amazon CodeGuru__ is a developer tool that provides intelligent recommendations to improve code quality and identify an application’s most expensive lines of code.
* __Amazon Kendra__ is an intelligent search service powered by machine learning.
* __Amazon Deep Learning AMIs__ provide machine learning practitioners and researchers with the infrastructure and tools to accelerate deep learning in the cloud, at any scale. 

* __Amazon SageMaker__ helps data scientists and developers to prepare, build, train, and deploy high-quality machine learning (ML) models
* __Amazon SageMaker Ground Truth__ is a fully managed data labeling service that makes it easy to build highly accurate training datasets for machine learning.
* __Amazon SageMaker Neo__ enables developers to optimize machine learning (ML) models for inference on SageMaker in the cloud and supported devices at the edge.
* __Amazon Augmented AI__ is a machine learning service which makes it easy to build the workflows required for human review.
