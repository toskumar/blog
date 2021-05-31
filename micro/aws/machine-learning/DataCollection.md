# Data Collection

### General Terminology
* __Traits of good data__ : `Large dataset` `precise attribute types, feature rich` `complete fields, no missing values` `values are consistent.` `Solid distribution of outcomes.` `Fair Sampling`
* Your should have atleast 10 times as many data points as the total number of features
* dataset = input data = training/test data
* column = attribute = feature
* row = observation = sample = data point
* Data set can be of any format like json, csv, video, audio or images
* __Structured Data__ : has a defined schema eg., rdbms table
* __Unstructured Data__ : has no defined schema eg., text, pdf, video, audio, images
* __Semi-Structured Data__ : has some organizational structure eg., csv, json or xml
* __Data Repository__
  * __Database__ : Store data in the form of tables with rows and columns, transactional  and strict schema.
  * __Data Warehouse__ : Data stored from many different data source including structured, unstructured, semi-structured data store. Processing done on import. data is classified stored with user in mind and easy to use with BI tools. 
  * __Data Lake__ : Massive amount of unstructured data into a single repository, no pre-processing done before storing data into data lake. Processing done on export, supports many different sources and formats.

### Machine Learning Data Terminology
* __Labeled Data (Supervised)__ : is data where we already know what the target attribute is. eg., an email is spam or not, images with a tag.
* __Unlabeled Data (Unsupervised)__ : is data that has been collected with no target attribute eg., customer information, tweets, log files
* __Categorical__ : Values are associated with a group, Qualitative, Discrete. eg., small, medium, large
* __Continuous__ : Values are measurable number, Quantitative, Continuous. eg., 7,9,11
* __Ground Truth__ : datasets refers to factual data that has been observed, successfully labeled and trusted as "truth" data.
* __Amazon SageMaker Ground Truth__ : AWS tool that helps build ground truth dataset by allowing different types of tagging/labelling process. Easily create labeled data.
* __Time Series Data__ : data refers to datasets that capture changes over time. eg., stock price.

### AWS Data Store
* __S3__ : unlimited storage, object based storage, go to place for storing machine learning data.
* __RDS__ : Relational database
* __Dynamo DB__ : no sql database or non relational database, key-value pair
* __Redshift__ : is a fully managed data warehouse solution to process peta bytes of data
  * __Redshift Spectrum__ : is a tool within Redshift to query redshift cluster which has sources in s3.
* __Timestream__ : is a fully managed time series database service which allows you to plugin BI tools for reporting.
* __Document DB__ : Document database eg., mongodb database 

### AWS Migration Tools
* __Data pipline__ : allows to process and move data from DynamoDB, RDS, Redshift to S3. support data transformation
* __Database Migration Service__ : transfers or migrates from one relational database to another database or S3.
* __Glue__ : is a fully managed ETL tool which transform and transfer data from one data source to another. Data format conversion is easy.

### Helper Tools
* __EMR__ : is a fully managed Hadoop cluster for distributed storage and compute.
* __Athena__ : allow user to directly query S3 or by AWS Glue data catalog

---

# Streaming Data Collection

### __Kinesis Family__
__Kinesis Data Streams__ : enables you to build custom applications that process or analyze large streaming data for specialized needs
  * Data producers(sensors, application logs) -> Kinesis Streams (Shard1,Shard2, ...) -> Data Consumers(EC2, EMR, Lambda, Kinesis Data Analytics) -> Storage and Analyzation (S3, DynamoDB, Redshift). 
  * Kinesis streams transfer or load or streams data. Shard is a container to hold data. Data consumers like lambda is used process and store the data into s3.
  * Each Shard consists of sequence of records, ingested at 1000 records per second. Default limit is 500 Shard can be incresed to unlimited. A record consist of partition key, sequence number and payload upto 1MB, data can be stored upto 24 hours and extended to 7 days.
  * KPL (Kinesis Producer Library) - allows to write to Kinesis Data Stream
  * KCL (Kinesis Consumer Library) - consumer and process data from Kinesis Data Stream
  * Kinesis API(AWS SDK) - low level api to send records to Kinesis Data Stream
  * When to use Kinesis Data Streams - Needs to be processed by consumers, Real time analytics, Feed into other service in real time, some action needs to occur in your data, Storing data is optional, Data retention is important.
  * Use Cases
    * To analyze system and application logs continuously and process within seconds
    * Run real time analytics on click stream  data and process it within seconds
    
__Kinesis Firehose__ :  is the easiest way to load streaming data into AWS
  * Data producers(sensors, application logs) -> Processing Tools (optional) Lambda -> Storage (S3, Redshift) [-> S3 event -> DynamoDB]
  * When to use Kinesis Firehose - Easily collect streaming data, processing is optional, Final destination is S3 or other datasource, Data retention is not important.
  * Use Cases
    * Capturing important data from IOT devices, embedded systems, consumer applications and storing it into a data lake.
    * Running ETL jobs on streaming data before stored into a datawarehouse  solution. 

__Kinesis Video Stream__ : is a service to allows video streams
  * Data producers(camera, audio) -> Data Consumers (EC2 continuous consumers, EC2 Batch consumers) -> Storage(S3)
  * Use Cases
    * Need to real time streaming video, audio data eg., detect objects in a video stream 
    * Batch process to store streaming data
    * Feed streaming data into other AWS services

__Kinesis Data Analytics__ : is the easiest way to process streaming data in real time with standard SQL
  * Streaming Input (Kinesis Data Stream, Kinesis Firehose) -> Kinesis Data Analytics -> Storage (S3, Redshift)
  * When to use Kensis Data Analytics
    * Run SQL queries on streaming data
    * Construct application that provide insight on your data
    * Create metrics, dashboards, monitoring, notification and alarms
    * Output query results into S3 or other AWS services

__Remember__
* Kinesis Data Streams and Kinesis Data Analytics cannot write data directly to S3. 
* Kinesis Data Firehose is used as the main delivery mechanism for outputting data into S3.
* PutRecords is a synchronous send function in Kinesis API(AWS SDK) used for critical events
* KPL implements send funtion asynchronously and incur an additional delay due to RecordMaxBufferedTime 
* KPL is easy to set up a retry mechanism, aggregate records to improve throughput, and automatically submits CloudWatch metrics
* The KPL must be installed as a Java application before it can be used with your Kinesis Data Streams
* A single shard can ingest up to 1 MB of data per second and process upto 1000 records per second
* A KPL user record is a blob of data that has particular meaning to the user.
* A Kinesis Data Streams record contains a partition key, sequence number, and a blob of data.
* __Batching__ refers to performing a single action on multiple items instead of repeatedly performing the action on each individual item.
  * __Aggregation__ – Storing multiple records within a single Kinesis Data Streams record.
  * __Collection__ – Using the API operation PutRecords to send multiple Kinesis Data Streams records to one or more shards in your Kinesis data stream.
