# Data Preparation
### Model
Taking a problem or challenge as described by lots of data, adding a machine learning algorithm and through computation, trying to figure out a mathematical formula that can accurately generalize about the problem.

Data > Algorithm > Computation> Feedback > Model > Generalization

    
### Developing a Good Model

  | | Supervised | Unsupervised | Reinforcement |
  | --- |  --- |  --- |  --- | 
  | Discrete | Classification | Clustering | Simulation-based Optimization|
  | Continuous | Regression | Reduction of Dimentionality | Autonomous Devices |

### Confusion Matrix
  
  |Predicted/Actual | True | False |
  | --- | --- | --- | 
  | True | I predicted correctly!        | I was wrong (False Positive)|
  | False| I was wrong. (False Negative) | I predicted Correctly! |

### Cascading Algorithm
__Problem__ What is the estimated basket size of shoppers who response to our email promotion ?

  `Remove outliers` -> `Identify relevant attributes` -> `Cluster into groups` -> `Predict basket size`

  `Random Cut Forest` -> `PCA` -> `K-Means` -> `Linear Learner` 

### Training and Test Data preparation
  * Training Data (70-80%)
  * Test Data (30-20%)
  * Randomize Split Strategy > Split > Train > Test
  * Sequential Split Strategy - works well for time series data
  * K-Fold Cross Validation Method - Randomize > Split > Fold > Train > Test > Repeat (Fold, Train Test) multiple times and test the result are approximate equal.
  
### SageMaker Modeling
  1. SageMaker Console
  1. SageMake SDK
  1. Jupyter notebook
  1. Apache Spark
 
* Most sagemaker algorithm accepts csv data eg., content-type=text/csv
* For unsupervised algorithm specify content-type=text/csv;label_size=0. Target value should be in the first column with no header. Notice that we need to specify the label size in the metadata value.
* 


