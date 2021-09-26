# Algorithm
[SageMaker Algorithms](https://docs.aws.amazon.com/sagemaker/latest/dg/algos.html)

`Unambiguous` specification of how to solve a class of problems. A set of steps to follow to solve a specific problem intended to be repeatable with the same outcome.

`Heuristic` A mental short-cut or "rule of thumb" that provides guidance on doing a task but does not guarantee a consistent outcome.

`Supervised Learning` A teacher or parent supervises the learning process by providing model examples and feedback on quizzes.

`Unsupervised Learning` You are totally unsupervised and must rely on alternative methods to learn other than prior experience.

`Reinforcement Learning` A model seeks to maximize reward, often through trial and error. We want to reinforce the desired behavior.

* Use SageMaker build-in algorithm
* Purchase from AWS marketplace
* Build your own via docker image.

### Regression
`Linear Leaner Algorithm` Liner models are supervised learning algorithms for regression, binary classification or multi-class classification problems. You give the model labels (x,y) with x being high-dimensional vector and y is a numeric label. The algorithm learns a linear function, or, for classification problems, a linear threshold function, and maps a vector x to an approximation of layer y.
To use this algorithm you need a number or list of numbers which yields some other number. the answer you're after. You can use it to predict a specific value or a threshold for grouping purposes.

```
y = ax + b

```

* __Adjust to minimize Error__ : The algorithm wants the equation to be as good of a fit as possible. Meaning the sum of all the instances from the training data point and line is as low as possible. One method is _Stochastic Gradient Descent_.
* __Very Flexible__ : Linear learner can be used to explore different training objectives and choose the best. Well suited for discrete or continuous inferences.
* __Built-in Tuning__ : Linear leaner algorithm has an internal mechanism for tuning hyper parameters separate from the automatic model tuning feature.
* __Good First Choice__ : If your data and objective meet the requirements, Linear Learner is a good first choice to try from your model. 
* __Use Cases__ : 
  * Predict quantitative value based on a given numeric input. Example: Based on last five years ROI from marketing spend, what can we expect to be this year's ROI?
  * Discrete Binary Classification Problem. Example: Based on past customer response, should I mail this particular customer? Yes or NO?
  * Discrete Multi-class Classification problems: Example: Based on past customer response, how should I reach this customer? Email, Direct Mail, or Phone Call?
  * Linear Learner works well for continuous data eg., 10,4,30,32,22,50... 
  * Sparse dataset or missing data set eg., 34,4, ,30,12, ,3, , 12) use Factorization Machines Algorithm

`Factorization Machines Algorithm` General purpose supervised learning algorithm for both binary classification and regression. Captures interactive between features with high dimensional sparse datasets. 
 
To use this algorithm you need a number or list of numbers which yields some other number. the answer you'are after. You can use it to predict a specific value or a threshold for placing into one of two groups. It is a good choice when you have "holes" in your data.

* __Considers only pair-wise features__ : Amazon SageMaker's implementation of factorization machines will only analyze relationships of two pairs of features at a time.
* __CSV is not supported__ : CSV is not a good choice for parse dimensions. File and pipe mode training are supported using recordIO-protobuf format with Float32 tensors.
* __Doesn't work for Multi-class problems__ : Factorization machines algorithm can be run in either binary classification mode or regression mode.
* __Really needs LOTS of data__ : To make up for the sparseness, needs lots of data. Recommended dimension of the input feature space is between 10,000 and 10,000,000
* __CPUs rock sparse data better__ : AWS recommends CPUs with factorization machines for the most efficient experience.
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
* __KNN is a lazy algorithm__ : Does not use training data points to generalize but rather uses them to figure out who's nearby.
* __Training data stays in memory__ : KNN doesn't learn but rather uses the training dataset to decide on similar samples.
* __Use Cases__
  * Credit Ratings : Group people together for credit risk based on attributes they share with others of known credit usage.
  * Product Recommendations : Based on what someone likes, recommend similar items they might also like.
  
### Image Analysis

Input (image) -> Image Analysis Model -> Output(label: dog, confidence:0.30) anything less than 70% score is not predictable.
* __Image Classification (Supervised)__ : Determine the classification of an image. It uses a convolutional neural network(ResNet) that can be trained from scratch or make use of transfer learning.
* __Object Detection (Supervised)__ : Detects specific objects in an image and assigns a classification with a confidence score.
* __Semantic Segmentation (Supervised)__ : Low level analysis of individual pixels and identifies shapes within an image.
  * Accepts PNG file input: You can submit files for training or inference in uncompressed PNG format
  * Only supports GPU instances for training: Due to the heavy computational power required GPU instances must be used for training.
  * Can deploy on either CPU or GPU instances: After training is done, model artifacts are output to S3. The model can be deployed as an end-point with either CPU or GPU instances.
* __Use Cases__:
  * Image Metadata Extraction : Extract scene metadata from an image provided an store it in a machine-readable format.
  * Computer Vision Systems : Recognize orientation of a part on an assembly line and, if required, issue an command to a robotic arm to re-orient the part.

### Anomaly Detection
Whats Different and What is the Same
`Random Cut Forest (Unsupervised)` Detect anamalous data points within a set, like spikes in time series data, breaks in periodicity or unclassifiable points. Useful way to find outliers when it's not feasible to plot graphically. TCF is designed to work with n-dimentional input.
Find occurrences in the data that are significantly beyond "normal" (usually more than 3 standard deviations) that could mess up your model training.
* __Gives an Anamaly scores to data points__ : Low scores indicate that a data point is considered _normal_ while high scores indicate the presence of an anomaly.
* __Scales Well__ : RCF scales very well with respect to number of features, data set size and number of instances.
* __Does not benefit from GPU__ : AWS recommends using normal compute instances (m1.m4,ml.c4)
* __Use Cases__
  * Quality Control : Analyze an audio test pattern played by a high end speaker system for any unusual frequencies.
  * Fraud Detection : If a financial transaction occurs for an unsual amount, unusual time or from an unusual place, flag the transaction from a closer look.

`IP Insights (Unsupervised) (SageMaker)` Learn usage patterns for IPv4 addresses by capturing associations between IP addresses and various entities such as user id or account numbers. 
Can potentially flag odd online behavior that might require closer review.
* Ingets Entity/IP address Pairs : Historic data can be used to learn baseline patterns
* Returns Inferences via a Score : When queried, the model will return a score that indicates how anomalous the entity/IP combination is, based on the baseline.
* Uses a Neural Network : Uses a neural network to learn latent vector representations for entities and IP addresses. 
* GPUs recommended for training : Generally, GPUs are recommended but if the dataset is large, distributed CPU instances might be more cost effective.
* CPUs recommended for Inference : Does not require costly GPUs for normal inference activities.
* __Use Cases__
  * Tiered Authentication Model : If a user tries to log into a website from an anomalous IP address, you might dynamically trigger an additional two factor authentication routine.
  * Fraud Detection : On a backing website, only permit certain activities if the IP address is unusual for a given user login

### Text Analytics

`Latent Dirichlet Allocation(LDA) (Unsupervised)` : LDA algorithm is an unsupervised learning algorithm that attempts to describe a set of observations as a mixture of distinct categories. LDA is most commonly used to discover a user-specified number of topics shared by documents within a text corpus. Here each observation is a document, the features are the presence (or occurrence count) of each word, and the categories are the topics. 
Used to figure out how similar documents are based on the frequency of similar words.
* __Use Cases__
  * Article Recommendation: Recommend articles on similar topics which you might have read or rated in the past.
  * Musical Influence Modeling : Explore which musical artists over time were truly innovative and those who were influenced by those innovators.

`Neural Topic Model (NTM) (Unsupervised)` : Unsupervised learning algorithm that is used to organize a corpus of documents into topics that contain word groupings based on their statistical distribution. Topic modeling can be used to classify or summarize documents based on the topics detected or to retrieve information or recommend content based on topic similarities.
Similar uses and function to LDA in that both NTM and LDA can perform topic modeling. However, NTM uses a different algorithm which might yield different results that LDA.

`Sequence to Sequence (Supervised)` : Supervised learning algorithm where the input is a sequence of tokens (for example, text, audio) and the output generated is another sequence of tokens.
Think a language translation engine that can take in some text and predict what that text might be in another language. We must supply training data and vocabulary.
* Steps consist of embedding, encoding and decoding: Using a neural network model (RNN and CNN), the algorithm uses layers for embedding, encoding and decoding into the target.
* Commonly initialized with pre-trained word libraries: A standard practice is initializing the embedding layer with a pre-trained word vector like FastText or Glove or to initialize it randomly and learn the parameters during training.
* Only GPU instances are supported: Currently Amazon SageMaker seq2seq is only supported on GPU instance types and is only set up to train on a single machine. But it does also offer support for multiple GPUs.
* __Use Cases__
  * Language Translations: Using a vocabulary, predict the translation of a sentence into another language.
  * Speech to Text: Given an audio _vocabulary_, predict the textual representation of spoken words.

`BlazingText (Supervised)(Unsupervised)` Highly optimized implementations of the Word2vec and text classification algorithms. The Word2vec algorithm is useful for many downstream natural language processing(NLP) tasks, such as sentiment analysis, named entity recognition, machine translation, etc.
Really, really optimized way to determine contextual semantic relationships between words in a body of text.

  | Modes | Word2Vec(Unsupervised) | Text Classification(Supervised)|
  | --- | --- | --- |
  | __Single CPU Instance__ | Continuous Bag of words, Skip-gram, Batch skip-gram | Supervised |
  | __Single GPU Instance__ (1 or more GPUs) | Continuous Bag of Words, Skip-gram | Supervised with 1 GPU |
  | __Multiple CPU Instances__ | Batch Skip-gram | None |
* Expect Single pre-processed text file : Each line in the file should contain a single sentence. If you need to train on multiple text files, concatenate them into one file and upload the file in the respective channel.
* Highly Scalable : Improves on traditional Word2Vec algorithm by supporting scale-out for multiple CPU instances. FastText text classifier can leverage GPU acceleration.
* Around 20x faster than FastText : Supports pre-trained FastText models but also can perform training about 20x faster than FastText
* __Use Cases__ 
  * Sentiment Analysis : Evaluate customer comments in social media posts to evaluate whether they have a positive or negative sentiment.
  * Document Classification : Review a large collection of documents and detect whether the document should be classified as containing sensitive data like personal information or trade secrets.
  
`Ojbect2Vec (Supervised)` General-purpose neural embedding algorithm that can learn low-dimensional dense embeddings of high-dimensional objects while preserving the semantics of the relationship between the pairs in the original embedding space.
A way to map out things in a d-dimentional space to figure out how similar they might be to one another.
* Expects pairs of things : Looking for pairs of items and whether they are _positive_ or _negative_ from a relationship standpoint. Accepts categorical labels or rating/score-based labels.
* Feature Engineering : Embedding can be used for downstream supervised tasks like classification or regression.
* Training data required : Officially, Object2Vec requires labeled data for training, but there are ways to generate the relationship labels from natural clustering.
* __Use Cases__
  * Movie rating prediction : Predict the rating a person is likely to give a movie based on similarity to other's movie rating
  * Document classification : Determine which genre a book is based on its similarity to known genre (history, thriller, biography, etc.)

### Reinforcement Learning
Reinforcement Learning is a machine learning technique that attempts to learn a strategy, called a policy, that optimizes for an agent acting in an environment. Well suited for solving problems where an agent can make autonomous decisions. Find the path to the greatest reward.

`Markov Decision Process` - Agent > Environment > Reward > State > Action > Observation > Episodes > Policy
DeepRacer project is an example for MDP.
* __Use Cases__
  * Autonomous Vehicles : A self-driving car model can _learn_ to stay on the road through iterations of trial and error in a simulation. Once the model is good enough, it can be tested in a real vehicle on a test track.
  * Intelligent HVAC Control : An RL model can learn patterns and routines of building occupants, impact of sunlight as it transitions across the sky and equipment efficiency to optimize the temperature control for lowest energy consumption.
 
### Forecasting
Past performance is not an indicator of future results.

`DeepAR (Supervised)` Forecasting algorithm for scalar times series using recurrent neural networks(RNN). DeepAR outperforms standard autoregressive integrated moving average (ARIMA) and exponential smoothing (ETS) by training a single model over multiple time series as opposed to each individual time series.
Can predict both point-in-time values and estimated values over a time frame by using multiple sets of historic data.
  | Forecast Type | Example |
  | --- | --- |
  | Point Forecast | Number of sneakers sold in a week in X |
  | Probabilistic Forecast | Number of sneakers sold in a week is between X and Y with Z% probability |

* Support for various time series : Time series can be numbers, counts, or values in an interval (such as temperature readings between o and 100)
* More time series is better : Recommend training a model on as many time series as are available. DeepAR really shines with hundreds of related time series.
* Must supply at least 300 observations : DeepAR requires a minimum number of observations across all time series.
* You must supply some hyper parameters : Context Length, Epochs, Predictions Length and Time Frequency are required hyper parameters.
* Automatic Evaluation of the Model : Uses a back test after training to evaluate the accuracy of the model automatically.
* __Use Cases__
  * Forecasting new product performance : Incorporate historical data from other products to create a model that can predict performance of a newly released product.
  * Predict labor needs for special events : Use labor utilization rates at other distribution centers to predict the required level of staffing for a brand new distribution center.

### Ensemble Learning
Using multiple learning algorithm and models collectively to hopefully improve the model accuracy.

`Extreme Gradient Boosting (XGBoost) (Supervised)` Open source implementation of the gradient boosted trees algorithm that attempts to accurately predict a target variable by combining the estimates of a set of simpler, weaker models. 
A virtual _Swiss army knife_ for all sorts of regression, classification and ranking problems, with 2 required and 35 optional hyper parameters to tune.
* Accepts CSV and libsvm for training and inference : Uses tabular data with rows representing observations, one column representing the target variable or label and the remaining columns representing features.
* Only trains on CPU and memory bound : Currently only trains on CPU instances and in memory bound as opposed to compute bound.
* Recommend lots of memory : AWS recommends using an instance with enough memory to hold the entire training data for optimal performance.
* Spark integration : Using the SageMaker Spark SDK, you can call XGBoost direct from within the spark environment.

`Decision Tree Ensembles` : We can create a set of classification and regression trees (CART) for each property eg., Location, age, size, number of bed rooms, number of bath rooms, condition, walk up or lift access, economic climate, lending climate.
* __Use Cases__
  * Ranking : On a n e-commerce website, you can leverage data about search results, clicks, and successful purchases, and then use XGBoost to train a model that can return relevance scores for searched products.
  * Fraud Detection : When XGBoost is given a dataset of past transactions and whether or not they were fraudulent, it can learn a function that maps input transaction data to the probability that transaction was fraudulent.
 

### Supervised Learning 
| Algorithm | Problem | 
| --- | --- |
| __Logistical Regression__ | To predict one of the two states, such as true or false | 
| __Multiclass Regression__ | Model is to predict a pre-defined set of values |
| __Linear Regression__ | Model is to predict a numerical value |
| __Factorization Machines Algorithm__ | is designed to capture interactions between features within high dimensional sparse datasets economically. |
| __Support Vector Machines__ | are a set of supervised learning methods used for classification, regression and outliers detection. |
| __XGBoost__ | Open source implementation of the gradient boosted trees algorithm that attempts to accurately predict a target variable by combining the estimates of a set of simpler, weaker models |
| __K-Nearest Neighbors (k-NN)__ | is an index based algorithm for classification and regression. Training has three steps sampling, dimension reduction and index building |
| __Object2Vec__ | is a general-purpose neural embedding algorithm that is highly customizable | 
| __DeepAR Forecasting__ | forecasting, time series using RNN|
| __Decision Trees__ | uses the tree representation to solve the problem in which each leaf node corresponds to a class label and attributes are represented on the internal node of the tree |
| __Random Forest__ | It is a collection of Decision Trees to solve Binary, Classification problems |

### Unsupervised Learning

| Algorithm | Problem |
| --- | --- |
| __Principal Component Analysis (PCA)__ |It lowers the dimensionality within a dataset by projecting data points onto the primary few principal components. The aim is to keep as much information or variation as possible | 
| __K-Means__ | It is used to finds discrete groupings within the dataset, where members of a group are as identical as possible to one another and as non-identical as possible from members of other groups.(Classification) | 
| __IP Insights__ | It is used to capture associations b/w IPv4 addresses and various entities | 
| __Random Cut Forest (RCF)__ | It identifies anomalous data points within a data set | 

### Textual Analysis

| Algorithm | Problem |
| --- | --- | 
| __BlazingText (Supervised)__  | It is a highly advanced application of the Word2vec and text classification algorithms that simply scale to large datasets. It is helpful for many downstream NLP tasks. | 
| __Sequence-to-Sequence (Supervised)__ | input and output is a sequence of token eg., text, audio | 
| __Latent Dirichlet Allocation (Unsupervised)__ | an algorithm used for determining topics in a set of documents. |
| __Neural Topic Model (Unsupervised)__ | used for determining topics in a set of documents, using a NN approach.| 

### Image Analysis (Supervised)

| Algorithm | Problem | 
| --- | --- | 
| __Image Classification__  | Determine the classification of an image. | 
| __Object Detection__ | It is used to classifies and detect objects in images using a single DNN (deep neural network)  | 
| __Semantic Segmentation__ | It's used to developing computer vision applications using a pixel-level, fine-grained approach. identifies shapes within an image.| 

### Reinforcement Learning

| Algorithm | Problem | 
| --- | --- | 
| __Markov Decision Process__ | MDPs aim to capture high-level details of a real problem that a learning agent encounters over some period of time in attempting to achieve some ultimate goal. | 

