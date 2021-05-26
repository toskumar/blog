# Algorithm
`Unambiguous` specification of how to solve a class of problems. A set of steps to follow to solve a specific problem intended to be repeatable with the same outcome.

`Heuristic` A mental short-cut or "rule of thumb" that provides guidance on doing a task but does not guarantee a consistent outcome.

`Supervised Learning` A teacher or parent supervises the learning process by providing model examples and feedback on quizzes.

`Unsupervised Learning` You are totally unsupervised and must rely on alternative methods to learn other than prior experience.

`Reinforcement Learning` A model seeks to maximize reward, often through trial and error. We want to reinforce the desired behavior.

* Use SageMaker build-in algorithm
* Purchase from AWS marketplace
* Build your own via docker image.

### Regression
`Liner Leaner Algorithm` Liner models are supervised learning algorithms for regression, binary classification or multiclass classification problems. You give the model labels (x,y) with x being high-dimensional vector and y is a numeric label. The algorithm learns a linear function, or, for classification problems, a linear threshold function, and maps a vector x to an approximation of layer y.
To use this algorithm you need a number or list of numbers which yields some other number. the answer you're after. You can use it to predict a specific value or a threshold for grouping purposes.

```
y = ax + b

```

* __Adjust to minimize Error__ : The algorithm wants the equation to be as good of a fit as possible. Meaning the sum of all the instances from the training data point and line is as low as possible. One method is _Stochastic Gradient Descent_.
* __Very Flexible__ : Linear learner can be used to explore different training objectives and choose the best. Well suited for discrete or continuous inferences.
* __Built-in Tuning__ : Linear leaner algorithm has an internal mechanism for tuning hyper parameters separate from the automatic model tuning feature.
* __Good First Choice__ : If your data and objective meet the requirements, Linear Learner is a good first choice to try from your model. 
* __Use Cases__: 
  * Predict quantitative value based on a given numeric input. Example: Based on last five years ROI from marketing spend, what can we expect to be this year's ROI?
  * Discrete Binary Classification Problem. Example: Based on past customer response, should I mail this particular customer? Yes or NO?
  * Discrete Multi-class Classification problems: Example: Based on past customer response, how should I reach this customer? Email, Direct Mail, or Phone Call?
  * Linear Learner works well for continuous data eg., 10,4,30,32,22,50... 
  * Sparse dataset or missing data set eg., 34,4, ,30,12, , 3, , 12) use Factorization Machines Algorithm

`Factorization Machines Algorithm` General purpose supervised learning algorithm for both binary classification and regression. Captures interactive between features with high dimensional sparse datasets. 
 
To use this algorithm you need a number or list of numbers which yields some other number. the asswer you'are after. You can use it to predict a specific value or a threshold for placing into one of two groups. It is a good choice when you have "holes" in your data.

* __Considers only pair-wise features__: Amazon SageMaker's implementation of factorization machines will only analyze relationships of two pairs of features at a time.
* __CSV is not supported__: CSV is not a good choice for parse dimensions. File and pipe mode training are supported using recordIO-protobuf format with Float32 tensors.
* __Doesn't work for Multi-class problems__: Factorization machines algorithm can be run in either binary classification mode or regression mode.
* __Really needs LOTS of data__: To make up for the sparseness, needs lots of data. Recommended dimension of the input feature space is between 10,000 and 10,000,000
* __CPUs rock sparse data better__: AWS recommends CPUs with factorization machines for the most efficient experience.
* __Don't perform well on dense data__ : Other algorithms are much more performant when you have a full set of data
* __High Dimensional Sparse Data Sets__ : Example: Click-stream data on which ads on a webpage ten to be clicked given known information about the person viewing the page.
* __Recommendations__ : Example: What short of movies should we commend to a person who has watched and rated some other movies?

### Clustering
Unsupervised algorithms that aims to group things such that they are with other things more similar than different.

`K-Means` Unsupervised algorithm that attempts to find discrete groupings within data, where members of a group are as similar as possible to one another and as different as possible from members of other groups. The Euclidean distance between these points represents the similarity of the corresponding observations.

K-Means will take in a list of things with attributes. You specify which attributes indicate similarity and the algorithm will attempt to group them together such that they are with other similar things. "Similarity" is calculated based on the distance between the identifying attributes.

* __Expects Tabular Data__ : Rows represent the observations that you want to cluster and the columns represent attributes of the observations.
* __Define the Identifying Attributes__ : You must know enough about the data set to propose attributes that will define similarity. If you have no idea, there are ways around this too.
* __Sage Maker uses a Modified K-Means__ : AWS uses a modified version of the web-scale K-Means algorithm, which it claims to be more accurate.
* __CPU Instances Recommended__ : GPU instances can be used but SageMaker's K-Means can only use one GPU.
* __Training is still a thing__ : You want to be sure you model is still accurate and using the best identifying attributes. Your data just doesn't have labels.
* __You define number of features and clusters__ : You must define the number of features for the algorithm to analyze and the number of clusters you want.

### Classification
`K-Nearest Neighbor` An index-based, non-parametric method for classification or regression. For classification, the algorithm queries the k points that are closest to the sample point and returns the most frequently used label as the predicted label. For regression, the algorithm queries the k closest points to the sample point and returns the average of the feature values as predicted value.

Predicts the value or classification based on that which you are closest. It can be used to classify or to predict a value (average value of nearest neighbors)

* __You choose the number of "neighbours"__ : You include a value for k, or in other words, the number of closest neighbors to use for classifying.
* __KNN is alazy algorithm__ : Does not use training data points to generalize but rather uses them to figure out who's nearby.
* __Training data stays in memory__ : KNN doesn't learn but rather uses the training dataset to decide on similar samples.
* __Use Cases__
  * Credit Ratings: Group people together for credit risk based on attributes they share with others of known credit usage.
  * Product Recommendations: Based onn what someone likes, recommend similar items they might also like.
  
### Image Analysis

Input (image) -> Image Analysis Model -> Output(label: dog, confidence:0.30) anything less than 70% score is not predictable.
* __Image Classification (Supervised)__ : Determine the classification of an image. It uses a convolutional neural network(ResNet) that can be trained from scratch or make use of transfer learning.
* __Object Detection (Supervised)__ : Detects specific objects in an image and assigns a classification with a confidence score.
* __Semantic Segmentation (Supervised)__ : Low level analysis of individual pixels and identifies shapes within an image.
  * Accepts PNG file input: You can submit files for training or inference in uncompressed PNG format
  * Only supports GPU instances for training: Due to the heavy computational power required GPU instances must be used for training.
  * Can deploy on either CPU or GPU instances: After training is done, model artifacts are output to S3. The model can be deployed as an endpoint with either CPU or GPU instances.
* Use cases:
  * Image Metadata Extraction: Extract scene metadata from an image provided an store it in a machine-readable format.
  * Computer Vision Systems: Recognize orientation of a part on an assembly line and, if required, issue an command to a robotic arm to re-orient the part.

