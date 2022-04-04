# Solution Architect Associate

## S3 - Simple Storage Service
* S3 is Object based storage. 
* Files are stored in buckets, file size can be 0 to 5 TB and provides unlimited storage capacity.
* S3 is a universal namespace means bucket name must be globally unique. eg., https://acg.s3.amazonaws.com , https://acg.eu-west-1.amazonaws.com
  * Key - this is simply the name of the object
  * Value - this is simply the data and is made up of a sequence of bytes
  * Version ID - important for versioning
  * Metadata - Data about data you are storing
  * Sub-resources - ACL and Torrent
* Read after write consistency of news files and Eventual consistency for overwrite of PUT and DELETE
* Restricting Bucket Access
  * Bucket policies - applies across the whole bucket
  * Object policies - applies to individual files
  * IAM policies - applies to users and groups
* S3 availability - 99.99% and durability - 99.999999999%
* S3 One Zone Infrequent Access - low cost, infrequently accessed data and does not require multiple availability zone.
* S3 IA - Infrequently Accessed - data is accessed less frequently but requires rapid access when needed. Low fees than S3 but charged for retrieval fee.
* S3 Intelligent Tiering - data is automatically moved to the most effective access tier.
* S3 Glacier - secure, durable, low cost storage class for data archiving. Retrieval times configurable from minutes to hours.
* S3 Glacier Deep Archive - low cost storage class where the retrieval time of 12 hours is acceptable.

