# Data Preparation
### Model
Taking a problem or challenge as described by lots of data, adding a machine learning algorithm and through computation, trying to figure out a mathematical formula that can accurately generalize about the problem.

Data > Algorithm > Computation> Feedback > Model > Generalization

    
### Developing a Good Model

  | | Supervised | Unsupervised | Reinforcement |
  | --- |  --- |  --- |  --- | 
  | Training | Training data and Testing data | No Training | How to maximize reward |
  | Discrete | Classification | Clustering | Simulation-based Optimization|
  | Continuous | Regression | Reduction of Dimentionality | Autonomous Devices |

### Confusion Matrix
  
  |Actual/Predicted | True | False |
  | --- | --- | --- | 
  | True | I predicted correctly! (True Positive)        | I was wrong (False Positive) (Incorrectly predicted a positive case) (Type I error)|
  | False| I was wrong. (False Negative) (Incorrectly predicted a negative case) (Type II error) | I predicted Correctly! (True Negative) |

### Cascading Algorithm
__Problem__ What is the estimated basket size of shoppers who response to our email promotion ?

  `Remove outliers` -> `Identify relevant attributes` -> `Cluster into groups` -> `Predict basket size`

  `Random Cut Forest` -> `PCA` -> `K-Means` -> `Linear Learner` 

### Training and Test Data preparation
  * Training Data (70-80%)
  * Test Data (30-20%)
  * Randomize > Split > Train > Test
  * Sequential Split Strategy - works well for time series data
  * Split Strategy - 
  * K-Fold Cross Validation Method - Randomize > Split > Fold > Train > Test > Repeat (Fold, Train Test) multiple times and test the result are approximate equal.
  * For optimal performance, the optimized protobuf recordIO format is recommended. Take advantage of pipe mode and data can be streamed from S3 to the learning instance requiring less EBS space and faster start-up.
* Create Training job api
  * High level python library provided by amazon SageMaker 
  * Use of SDK for python
* Hyperparameter - values set before the learning process.
* Parameter - values derived via the learning process/
  
### SageMaker Modeling
  1. SageMaker Console
  1. SageMake SDK
  1. Jupyter notebook
  1. Apache Spark
 
* Most sagemaker algorithm accepts csv data eg., content-type=text/csv
* For unsupervised algorithm specify content-type=text/csv;label_size=0. Target value should be in the first column with no header. Notice that we need to specify the label size in the metadata value.

### SageMaker Training
* Training Images - CreateTrainingJobAPI Call, uses CPU/GPU for computation
* Inference Images - CreateModel API Call for production, uses CPU/GPU for computation
* XGBoost implements an open source algorithm optimized for CPUs
