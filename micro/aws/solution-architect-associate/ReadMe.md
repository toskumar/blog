# AWS Solution Architect Associate

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

### Storage Tiers  
* S3 Standard
* S3 One Zone Infrequent Access - low cost, infrequently accessed data and does not require multiple availability zone.
* S3 IA - Infrequently Accessed - data is accessed less frequently but requires rapid access when needed. Low fees than S3 but charged for retrieval fee.
* S3 Intelligent Tiering - data is automatically moved to the most effective access tier.
* S3 Glacier - secure, durable, low cost storage class for data archiving. Retrieval times configurable from minutes to hours.
* S3 Glacier Deep Archive - low cost storage class where the retrieval time of 12 hours is acceptable.

### Encryption
* Encryption at transit using SSL/TLS
* Encryption at rest 
  * SSE-S3 Server side encryption using AWS managed keys
  * SSE-KMS Server side encryption using keys managed by both AWS and customer
  * SSE-C Server side encryption using customer provided keys
  * Client Side Encryption where client encrypt the file and upload into S3

### Life-cycle management
Objects can be stored cost effectively though the life cycle management. It is a a set of rules that define actions that S3 applies to a group of objects. For example, you might choose to transition objects to the S3 Standard to IA storage class 30 days after creating them, or archive objects to the S3 Glacier after 90 days.

### Object Version
* Versioning means keeping multiple variants of an object in the same bucket. 
* Once versioning is enabled it can't be disabled but can be suspended.
* When an object is deleted, s3 insert a delete marker instead of deleting the object.
* We can optionally add another layer of security by configuring a bucket to enable MFA delete
* Object versions can be deleted whenever you want, when you delete the 'delete marker' then the next latest version becomes available.

### Object Lock
* S3 Object lock stores objects using a WORM (Write Once Read Many) model. It helps prevents objects being delete or modified for a fixed amount of time of indefinitely. 
  * Governance Mode - User can't overwrite or delete object version or alter its lock settings unless they have special permission.
  * Compliance Mode - a protected object can't be overwritten or deleted by any user including the root user.
  * Retention period protect an object version for a fixed amount of time.
  * Legal hold  prevents an object version from being overwritten or deleted. User with S3:PutObjectLegalHold permission can place or remove legal hold on object.
* S3 Glacier Vault Lock allows user to easily deploy and enforce compliance controls for individual S3 Glacier vaults with a Vault Lock policy. 

### Performance
* You can read 5500 GET request per second per prefix. Better performance can be acheived by spreading your read across different prefixes.
* Use multipart upload for files more than 100 MB (recommended) and required for files more than 5GB
* Download using byte range fetches.

### Select
* S3 select enables applications to retrieve only a subset of data from an object (csv,json,zip containing csv) by using simple SQL expression.
* Glacier select allows you to run SQL queries against Glacier directly.

### AWS Organization
AWS Organization is an account management service that enables you to consolidate multiple AWS accounts into an organization that you create and centrally manage.
* Paying account should be used for billing purpose only, other Org units accounts can be linked to this paying account for consolidated billing.
* Service Control Policies - Either OrgUnit or individual accounts services can be enabled or disabled
* Tag Policies are a type of policy that can help you standardize tags across resources in your organization's accounts.

### Cross Account Access
* Using Bucket policies & IAM (applies across the entire bucket) - Programmatic access only
* Using Bucket ACL and IAM (individual objects). Programmatic access only
* Cross account IAM roles. Programmatic and console access.

### Cross region replication
* Versioning must be enabled on both the source and destination buckets
* Files in an existing bucket are not replicated automatically.
* All subsequent updated files will be replicated automatically.
* Delete markers are not replicated
* Deleting individual version or delete markers will not be replicated.
* Make public action does not get replicated to target bucket.