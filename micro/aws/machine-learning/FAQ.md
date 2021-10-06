# Machine Learning FAQ

* __Regression__ model is to predict a numerical value
* __Multiclass__ model is to predict a pre-defined set of values
* __Binary__ model is to predict one of the two states, such as true or false 

* __Batch Prediction__ a set of observations that can run all at once
* __Real-time Prediction__ are for applications with a low latency requirement, such as interactive web, mobile, or desktop applications.

* __Machine Learning Situations__ when you can't code the rules and you can't scale.

* __Feature Engineering__ 
  * __Feature engineering__ is the process of using domain knowledge to extract features from raw data.
  * __Feature selection__ is the process of selecting a subset of relevant features for use in model
  * __Replace missing data__ is knows as imputation. 
    * Replace missing data with mean or median for numeric feature and there is no correlation between feature. 
    * Use supervised learning algorithm like KNN, Multivariate Imputation by Chained Equation (MICE), Deep Learning when there is correlation between feature.
  * __Forming Cartesian products__ of one variable with another variable eg., variable A, B, C with Z => A_Z, B_Z and C_Z 
  * __Binning__ numeric variables to categories eg., the continuous numeric feature age is not linearly correlated with the likelihood to purchase a book
  * __Domain-specific__ features eg., l, b, h and introduce v=l*b*h
  * __Variable-specific__ a sentence has generic ways of processing. eg., forming n-grams from text “the fox jumped over the fence”
* __Feature Scaling__
  * __Normalization__ is a scaling technique in which values are shifted and rescaled, range between 0 and 1. X'=[X-X(min)]/[X(max)-X(min)]
  * __Standardization__ is another scaling technique where the values are centered around the mean with a unit standard deviation. X'=(X-X')/SD

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

## Evaluate Model Accuracy
* __AUC__ Area Under the ROC Curve (AUC) measures the ability of a binary ML model to predict a higher score for positive examples as compared to negative examples. Prediction range is 0 to 1. Precision, Recall and Accuracy must be higher value and FPR shall be a smaller value. 

* __Macro-averaged F1-score__ The macro-averaged F1-score is used to evaluate the predictive performance of multiclass ML models. 
  * __F1 Score__ = (2 * Precision * Recall)/ (Precision + Recall) - Prediction range is 0 to 1, where larger value indicates a better prediction. 
  * __Macro Average F1 Score__ = average (F1 Score) - Prediction range is 0 to 1, where larger value indicates a better prediction.

* __RMSE__ 	The Root Mean Square Error (RMSE) is a metric used to evaluate the predictive performance of regression ML models.
  * RMSE = SQRT(AverageOf(squareOf(actual-predicted)))

* __Cut-Off__ Conversion of a numeric prediction score into a 0 or 1 label 

* __Underfitting__ the training data when the model performs poorly on the training data.

* __Overfitting__ your training data when you see that the model performs well on the training data but does not perform well on the evaluation data.

* __Retraining Model__ It is a good practice to continuously monitor the incoming data and retrain your model on newer data if you find that the data distribution has deviated significantly from the original training data distribution. A simpler strategy is to train the model periodically, for example, daily, weekly, or monthly.

* __Confusion Matrix__

  |Actual/Predicted | Predicted True | Predicted False | |
  | --- | --- | --- | --- | 
  | __Actual True__ | I predicted correctly! (True Positive)     | I was wrong (False Positive) (Incorrectly predicted a positive case) (Type I error) | Precision = TP/(TP+FP) |
  | __Actual False__ | I was wrong. (False Negative) (Incorrectly predicted a negative case) (Type II error) | I predicted Correctly! (True Negative)| - |
  | | Recall = TP/(TP+TN) | FPR=FP/(FP/TN) or TNR=TN/(TN+FP) | Accuracy = (TP + TN)/(TP+FP+FN+TN) |
  * __Accuracy__ measures the percentage of correct predictions. Accuracy = (TP + TN)/(TP+FP+FN+TN)
  * __Precision__ Precision shows the percentage of actual positive instance. Precision = TP/(TP+FP)
  * __Recall (Sensitivity or TPR)__ Recall shows the percentage of actual positives among the total number of relevant instances. Recall = TP/(TP+FN)
  * __False Positive Rate (Specificity)__ measures the false alarm rate or the fraction of actual negatives that are predicted as positive. FPR = FP/(FP+TN) 

## ML Framework
* __TensorFlow__ is a ML Framework developed by __Google__ and __Keras__ is an opensource API interface for TersorFlow 
* __MXNet__ is a ML/DL Framework developed by __AWS and Microsoft__ and __Gluon__ is an opensource API interface for MXNet  
* __PyTorch__ is an opensource library used by Facebook AI research lab.
* __Scikit Learn__ is the most useful and robust library for machine learning in Python.
* __Apache Spark__ used for preprocessing data. Apache Spark library is available in both Python and Scala, that can be used to train models in SageMaker.
* __Hugging Face__ Amazon SageMaker enables customers to train, fine-tune, and run inference using Hugging Face models for Natural Language Processing (NLP) on SageMaker
* __Chainer__ SageMaker to train and deploy a model using custom Chainer code
* __R__ SageMaker notebook instances support R using a pre-installed R kernel

## ML File format 
* __File Mode__ Load data from S3 to training instance volume
* __Pipe Mode__ Stream data from S3 using recordIO-protobuf
* __RecordIO__ is a binary data exchange format where data is divided into chunks called records and prepend its length followed by the data.
* __Parquet__ column-oriented data storage format of the Apache Hadoop ecosystem. 

## AWS AI and ML Services

* __Amazon Lex__ is a service for building conversational interfaces into any application using voice and text.
* __Amazon Polly__ is a service that turns text into lifelike speech, allowing you to create applications that talk, and build entirely new categories of speech-enabled products. Supports Speech Synthesis Markup Language (SSML) tags which can adjust the speech rate, pitch or volume. Also supports pronunciation lexicons to customize the pronunciation of words.
* __Amazon Translate__ is a neural machine translation service that delivers fast, high-quality, affordable, and customizable language translation. 
* __Amazon Textract__ is a machine learning service that automatically extracts text, handwriting and data from scanned documents that goes beyond simple optical character recognition (OCR) to identify, understand, and extract data from forms and tables.
* __Amazon Transcribe__ makes it easy for developers to add __speech to text__ capabilities to their applications.
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
* __AWS PrivateLink__ provides private connectivity between VPCs, AWS services, and your on-premises networks, without exposing your traffic to the public internet. AWS PrivateLink makes it easy to connect services across different accounts and VPCs to significantly simplify your network architecture.
* __VPC endpoint__ enables connections between a virtual private cloud (VPC) and supported services, without requiring that you use an internet gateway, NAT device, VPN connection, or AWS Direct Connect connection. Therefore, your VPC is not exposed to the public internet.  A VPC endpoint for Amazon S3 is a logical entity within a VPC that allows connectivity only to Amazon S3. 

### Data transformation
* __N-gram Transformation__ ngram(var1, 2) = {"I really enjoined"} = {"I really", "really enjoined", "I", "really", "enjoined"} 
* __Orthogonal Sparse Bigram (OSB) Transformation__ osb(var1, 3) = {"I really enjoined"} = {"I_really", "I__enjoined", "really_enjoined"}
* __Lowercase Transformation__ lowercase(var1) = {"I Really Enjoined"} = {"i really enjoined"}	
* __Remove Punctuation Transformation__ no_punct(var1) = {"please - fasten your seat-belts!"} = {"please", "fasten", "your", "seat-belts"}
* __Quantile Binning Transformation__ The purpose is to discover non-linearity in the variable's distribution by grouping observed values together
* __Normalization Transformation__ The normalization transformer normalizes numeric variables to have a mean of zero and variance of one.
* __Cartesian Product Transformation__ {"A", "B", "C"}X{"Z"} = {"A_Z", "B_Z", "C_Z"}

### ML to S3 permission
* To read data from S3 Grant __GetObject__ and __ListBucket__ permission
* To write into S3 Grant __GetObject__ , __PutObject__ , __PutObjectAcl__ and __ListBucket__

### Amazon SageMaker

* Amazon SageMaker is a fully managed machine learning service. With SageMaker, data scientists and developers can quickly and easily build and train machine learning models, and then directly deploy them into a production-ready hosted environment.

* __SageMaker Model building steps__
__Prepare__ - Data Wrangler, Feature Store, Ground Truth, Clarify
__Build__ - Studio, AutoPilot, JumpStart
__Train & Tune__ - Experiment, Debugger, Distributed Training
__Deploy & Manage__ - Pipelines, Model Monitor, Kubernetes Integration, Edge Manager, Neo
 

* __SageMaker Features__
  * __SageMaker Studio__ - An integrated machine learning environment where you can build, train, deploy, and analyze your models all in the same application.
  * __SageMaker Model Registry__ - Versioning, artifact and lineage tracking, approval workflow, and cross account support
  * __SageMaker Projects__ - Create end-to-end ML solutions with CI/CD by using SageMaker projects.
  * __SageMaker Model Building Pipelines__ - Create and manage machine learning pipelines integrated directly with SageMaker jobs.
  * __SageMaker ML Lineage Tracking__ - creates and stores information about the steps of a machine learning (ML) workflow from data preparation to model deployment. 
  * __SageMaker Data Wrangler__ - Import, analyze, prepare, and featurize data in SageMaker Studio.
  * __SageMaker Feature Store__ - A centralized store for features and associated metadata so features can be easily discovered and reused. Two type of stores - online(realtime) and offline(batch) inference
  * __SageMaker JumpStart__ - Learn about SageMaker features and capabilities through curated 1-click solutions, example notebooks, and pretrained models that you can deploy.
  * __SageMaker Clarify__ - Improve your machine learning models by detecting potential bias and help explain the predictions that models make.
  * __SageMaker Edge Manager__ - Optimize custom models for edge devices, create and manage fleets and run models with an efficient runtime.
  * __SageMaker Ground Truth__ - High-quality training datasets by using workers along with machine learning to create labeled datasets.
  * __Amazon Augmented AI__ - Build the workflows required for human review of ML predictions.
  * __SageMaker Studio Notebooks__ - The next generation of SageMaker notebooks that include AWS Single Sign-On (AWS SSO) integration, fast start-up times, and single-click sharing.
  * __SageMaker Experiments__ - Experiment management and tracking.
  * __SageMaker Debugger__ - Inspect training parameters and data throughout the training process.
  * __SageMaker Autopilot__ - Users without machine learning knowledge can quickly build classification and regression models. Autopilot supports 2 built-in algorithms at launch: XGBoost and Linear Learner.
  * __SageMaker Model Monitor__ - Monitor and analyze models in production (endpoints) to detect data drift and deviations in model quality.
  * __SageMaker Neo__ - Train machine learning models once, then run anywhere in the cloud and at the edge.
  * __SageMaker Elastic Inference__ - Speed up the throughput and decrease the latency of getting real-time inferences.
  * __Reinforcement Learning__ - Maximize the long-term reward that an agent receives as a result of its actions.
  * __Preprocessing__ - Analyze and preprocess data, tackle feature engineering, and evaluate models.
  * __Distributed training__ libraries automatically split large deep learning models and training datasets across AWS GPU instances in a fraction of the time
  * __Batch Transform__ - Preprocess datasets, run inference when you don't need a persistent endpoint, and associate input records with inferences to assist the interpretation of results.
  * __Authentication__ - Onboard SageMaker Studio using SSO Authentication or IAM Authentication
  * __VPC__ - SageMaker Studio uses two VPCs. One VPC is managed by Amazon SageMaker and provides direct internet access. You specify the other VPC, which provides encrypted traffic between the domain and your Amazon Elastic File System (EFS) volume.
  * __Kubernetes__ is an open source system used to automate the deployment, scaling, and management of containerized applications. 
  * __Kubeflow__ Pipelines is a workflow manager that offers an interface to manage and schedule machine learning (ML) workflows on a Kubernetes cluster. 
  * __Automatic Model Tuning__ is supported in SageMaker for all built-in algorithm and arbitrary algorithm through Docker images. Bayesian Optimization is used a Model tuning algorithm.
 
  
### SageMaker Security
* __Security of the cloud__ – AWS is responsible for protecting the infrastructure that runs AWS services in the AWS Cloud.
* __Security in the cloud__ – Your responsibility is determined by the AWS service that you use.
* Access Control
  * Amazon SageMaker Studio notebooks and SageMaker notebook instances differ in their runtime environments.
	* Amazon SageMaker Studio uses filesystem and container permissions for access control and isolation of Studio users and notebooks. This is one of the major differences between Studio notebooks and SageMaker notebook instances. 
	* __User isolation__ on EFS - When you onboard to Studio, SageMaker creates an Amazon Elastic File System (EFS) volume for your domain that is shared by all Studio users in the domain. Each user gets their own private home directory on the EFS volume. This home directory is used to store the user's notebooks, Git repositories, and other data. To prevent other users in the domain from accessing the user's data, SageMaker creates a globally unique user ID for the user's profile and applies it as a POSIX user/group ID for the user’s home directory.
  * By default, when you create a notebook instance, users that log into that notebook instance have root access. If you don't want users to have root access to a notebook instance, when you call CreateNotebookInstance or UpdateNotebookInstance operations, set the RootAccess field to Disabled.
	* To protect your Amazon SageMaker Studio notebooks and SageMaker notebook instances, along with your model-building data and model artifacts, SageMaker encrypts the notebooks, as well as output from Training and Batch Transform jobs. SageMaker encrypts these by default using the AWS Managed Key for Amazon S3. For cross-account access use AWS KMS.
	* In Amazon SageMaker Studio, your SageMaker Studio notebooks and data can be stored in the following locations: S3, EBS, EFS
  * Amazon SageMaker ensures that machine learning (ML) model artifacts and other system artifacts are encrypted in transit and at rest
  * By default, Amazon SageMaker runs training jobs in an Amazon Virtual Private Cloud (Amazon VPC) to help keep your data secure. You can add another level of security to protect your training containers and data by configuring a private VPC.
	* __Internetwork Traffic Privacy__ - By default, API calls made to published endpoints traverse the public network to the request router. SageMaker supports Amazon Virtual Private Cloud interface endpoints powered by AWS PrivateLink for private connectivity between the customer's VPC and the request router to access hosted model endpoints.
	* __Identity-based policies__ are JSON permissions policy documents that you can attach to an identity, such as an IAM user, group of users, or role.
	* __Resource-based policies__ are JSON policy documents that you attach to a resource. Examples of resource-based policies are IAM role trust policies and Amazon S3 bucket policies. 
	* __Access control lists (ACLs)__ control which principals (account members, users, or roles) have permissions to access a resource.
	* Actions like passing a role between services are a common function within SageMaker.You pass the role (iam:PassRole) when making these API calls.
	* Amazon SageMaker Studio and SageMaker notebook instances allow direct internet access by default. You can choose to restrict which traffic can access the internet by launching your Amazon SageMaker Studio and SageMaker notebook instances in a Amazon Virtual Private Cloud (Amazon VPC).
	* To control access to your data and job containers, we recommend that you create a private VPC and configure it so that they aren't accessible over the internet.

### SageMaker Monitoring
* __Amazon CloudWatch__ monitors your AWS resources and the applications that you run on AWS in real time. You can collect and track metrics, create customized dashboards, and set alarms that notify user. For example, you can have CloudWatch track CPU usage or other metrics of your Amazon EC2 instances and automatically launch new instances when needed. 

* __Amazon CloudWatch Logs__ enables you to monitor, store, and access your log files from EC2 instances, AWS CloudTrail, and other sources. 

* __AWS CloudTrail__ captures API calls and related events made by or on behalf of your AWS account and delivers the log files to an Amazon S3 bucket that you specify. You can identify which users and accounts called AWS, the source IP address from which the calls were made, and when the calls occurred.

* __Amazon EventBridge__ monitors status change events in Amazon SageMaker. EventBridge enables you to automate SageMaker and respond automatically to events such as a training job status change or endpoint status change. Events from SageMaker are delivered to EventBridge in near real time. You can write simple rules to indicate which events are of interest to you, and what automated actions to take when an event matches a rule.

* __Amazon SageMaker__ provides APIs, SDKs, and a command line interface that you can use to create and manage notebook instances and train and deploy models.