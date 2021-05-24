# Data Preparation

Data preparation is the process of transforming a data set using different techniques to prepare it for model training and testing. Changing our dataset so it is ready for Machine Learning.

### Categorical Encoding

Categorical Encoding is a process of manipulating categorical variables when ML algorithm expect numerical values as inputs. Changing category values in our dataset to numbers. Example of Categorical encoding 
  * Color {green, purple, blue} - Nominal means order does not matter
  * Evil {true, false} - Nominal means order does not matter
  * Size {L > M > S} - Ordinal means order does matter

* Encoding Categorical Features to predict a loan will be approved or not
  | ID | Type | Bedrooms | Area | Pool Size | Price | Loan Approved |
  | --- | --- |  --- | --- | --- | --- | --- | 
  | 1 | condo    | 2 | 2345 | S | 250230 | N |
  | 2 | house    | 4 | 3100 | L | 243679 | Y |
  | 3 | apartment| 2 | 1250 | M | 120300 | Y |
  | 4 | house    | 4 | 2250 | N | 220300 | N |
  * No need to encode Bedrooms, Area and Price as they are numerical values
  * Loan Approved (Categorical Nominal) is our target attributes and encode as N -> 0 and Y -> 1
  * Pool size (Categorical Ordinal) is an Ordinal values N -> 0, S-> 5, L -> 10, M -> 7
  * House type(Categorical Nominal) is a nominal value and need to use some encoding technique like one-hot encoding condo -> 1-0-0 (CondoType, HouseType, ApartmentType)
  * One hot encoding - Transforms nominal categorical features and creates new binary column  for each observation. Adding a column to your dataset of 1 or 0

### Feature Engineering
Transforming attributes within our data to make them more useful within our model for the problem at hand. Feature engineering is also compared to an art.

__Text Feature Engineering__ : Transforms text within our data so Machine Learning algorithms can better analyze it. Splitting text into bite size pieces.

* __Bag of words__ : Tokenize raw text and create a statistical representation of text. Breaks up text by white space into single word. "He will save us" = {"He", "will", "save", "us"}
 
* __N-Gram__ : An extension of Bag of Words which produces group of words of n size. Break up text by white space into group of words. eg., 2-Gram "He will save us" = {"He will", "will save", "save us", "He", "will", "save", "us}. Unigram = 1 word token, Bigram = 2 word token, trigram = 3 word token

* __Orthogonal Sparse Bigram (OSB)__ : Creates group of words of size n and outputs every pair of words that includes the first word. Create groups of words that always include the first word. eg., OSB, size=4 "He will save us" = {"he_will", "he__save", "he___us"}

* __Term Frequency - Inverse Document Frequency (TF-IDF)__ : Represents how important a word or words are to a given set of text by providing appropriate weights to erms that are common and less common in the text. Show us the popularity of a word or words in text data by making common words like "the" and "and" less important.
    | Doc1 Word | Count| Doc 2 Word | Count |
    | --- | --- |  --- | --- |
    | the  | 3  | the  |  2  |
    | force| 1  | save |  1  |
  * TF-IDF Vectorizer (2,7) where 2 is the number of documents and 7 is number of unique N-gram

* __Remove Punctuation__ : Sometimes removing punctuation is a good idea if we do not need them.

* __Lowercase Transformation__ : Using lowercase transformation can help standardize raw text.

* __Cartesian Product Transformation__ : Creates a new feature from the combination of two or more text or categorical values. Combining sets of words together.
  | Textbook | binding | cartesian_product |
  | --- | --- | --- |
  | Python Data Science | Softcover | {"Python_Softcover", "Data_Softcover", "Science_Softcover"} |
  | Machine Learning | Hardcover | {"Machine_Hardcover", "Learning_Hardcover"}|

* __Feature Engineering Dates__ : Translating dates into useful information.
  | Date | is_weekend | day_of_week | month | year |
  | --- | --- | --- | --- | --- | 
  | 2015-06-17 | 0 | 2 | 6 | 2015 |
  | 2015-03-14 | 1 | 5 | 3 | 2015 |

### Numberic Feature Engineering
Transforming numeric values within our data so Machine Learning algorithms can better analyse them. Changing numberic values in our datasets so they are easier to work with eg., large values. Can always scale back to the original values.
* __Feature Scaling__ : Changes numeric values so all values are on the same scale
  * __Normalization__  x'=(x-min(x))/(max(x)-min(x)), rescales value between 0 to 1
  * __Standardization__ Z=(x-x')/SD where x' is the mean value, 0 is the average value, rescaled values is less affected by outliers. 
* __Binning__ : Changes numeric values into groups or buckets of similar values. 
  * __Quantile Binning__ aims to assign the same number of features to each bin.

### Other Feature Engineering
* __Image Feature Engineering__ : Extracting useful information from images before using them with ML algorithms. Transforming images to find out useful information.
* __Audio Feature Engineering__ : Extracting useful information from sounds and audio before using them with ML algorithms. Transforming audio data into somthing useful.
* __Data Formats__ 
  * __File Mode__ : Loads all of the data from S3 directly onto the training instance volumes eg., CSV, JSON, Parquet, Image files (.png or .jpg) 
  * __Pipe Mode__ : Your datasets are streamed directly from Amazon S3. recordIO-protobuf (creates tensor multi-dimentional array). Faster training and better throughput using recrodIO-protobuf tensors.

### Hanlding Missing Values
Missing values in your dataset can be just as frustrating and interfere with analysis and your models prediction. Missing data can be represented in many different ways (null, NaN,NA, None, etc.) Replacing missing values is known as Imputation.

* Missing at Random (MAR) - means that the prepensity for a data point to be missing is not releated to the missing data but it is related to some of the observed data
* Missing Comletely at Random (MCAR) - the fact that a certain value is missing has nothing to do with its hypothetical value and with the values of other variables. 
* Missing not at Random (MNAR) - two possible reasons are that the missing value depnds on the hypothetical value or missing value is dependent on some other variable's value. 

* Techniques for replacing missing values 
  * Supervised learning - predicts missing values based on the values of other features. Most difficult but can yield best result.
  * Mean - the average value
  * Median - orders values then chooses value in the middle
  * Mode - most common value
  * Drop rows - removes missing values

### Feature Selection
* __Feature Selection__ : Selecting the most relevant features from your data to prevent over-complicating the analysis, resolving potential inaccuracies, and removes irrelevant features or repeated information. Deciding what to keep and what to get rid of.

* __Principle Component Analysis(PCA)__ : An unsupervised learning algorithm that reduces the number of features while still retaining as much information as possible. Reduces the total number of features in a dataset. Use this technique when the data is too large due to the large number of features.

### AWS Helper Tools
  * AWS Glue : Source (S3, DynamoDB, RDS, Redshift, EC2) -> Crawler -> Data Catalog -> Job (Scala, Python) -> Destination(S3, EMR, Redshift, Athena). 
  * Sage Maker - use Jupyter notebook and python/scala for data transformation  
  * EMR - Transform petabytes of distributed data and output data into S3
  * Athena - Query data catalog and output result into S3
  * Data Pipeline - Transforms data from EC2 instance and output data into S3
  
