# Data Collection 

## General Terminology
* __Traits of good data__ : `Large dataset` `precise attribute types, feature rich` `complete fields, no missing values` `values are consistent.` `Solid distribution of outcomes.` `Fair Sampling`
* Your should have atleast 10 times as many data points as the total number of features
* dataset = input data = training/test data
* column = attribute = feature
* row = observation = sample = data point
* Data set can be of any format like json, csv, video, audio or images
* __Structured Data__ : has a defined schema eg., rdbms table, xml
* __Unstructured Data__ : has no defined schema eg., text, pdf, video, audio, images
* __Semi-Structured Data__ : has some organizational structure eg., csv, json or xml
* __Data Repository__
  * __Database__ : Store data in the form of tables with rows and columns, transactional  and strict schema.
  * __Data Warehouse__ : Data stored from many different data source including structured, unstructured, semi-structured data store. Processing done on import. data is classified stored with user in mind and eady to use with BI tools. 
  * __Data Lake__ : Massive amount of unstructured data into a single repository, no pre-processing happens before storing data into data lake. Processing done on export, many different sources and formats.

## Machine Learning Data Terminology
* __Labeled Data (Supervised)__ : is data where we already know what the target attribute is. eg., an email is spam or not, images with a tag.
* __Unlabeled Data (Unsupervised)__ : is data that has been collected with no target attribute eg., customer information, tweets, log files
* __Categorical__ : Values are associated with a group, Qualitative, Discrete. Remember (l) in categorical and qualitative. Breed of a dog is Qualitative.
* __Continuous__ : Values are measurable number, Quantitative, Continuous. Remember (i) in continuous and qualitative. Height and weight of a dog is Quantitative.
* __Ground Truth__ : datasets refers to factual data that has been observed, successfully labeled and trusted as "truth" data.
* __Amazon SageMaker Groun Truth__ : AWS tool that helps build ground truth dataset by allowing different types of tagging/labelling process. Easily create labeled data.
* __Time Series Data__ : data refers to datasets that capture changes over time. eg., stock price.

## AWS Data Store
* __S3__ : unlimited storage, object based storage, go to place for storing machine learning data.
* __RDS__ : Relational database
* __Dynamo DB__ : no sql database or non relational database, key-value pair
* __Redshift__ : is a fully managed data warehouse solution to process peta bytes of data
  * __Redshift Spectrum__ : is a tool within Redshift to query redshift cluster which has sources in s3.
* __Timestream__ : is a fully managed time series database service which allows you to plugin BI tools for reporting.
* __Document DB__ : Document database eg., mongodb database 

## AWS Migration Tools
* __Data pipline__ : allows to process and move data from DynamoDB, RDS, Redshift to S3. support data transformation
* __Database Migration Service__ : transfers or migrates from one relational database to another database or S3.
* __Glue__ : is a fully managed ETL tool which transform and transfer data from one data source to another. Data format conversion is easy.

## Helper Tools
* __EMR__ : is a fully managed Hadoop cluster for distributed computing and storage
* __Athena__ : allow user to directly query S3 data or AWS Glue data catalog


