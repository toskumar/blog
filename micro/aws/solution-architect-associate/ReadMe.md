# AWS Solution Architect Associate

## IAM
### AWS Organization
AWS Organization is an account management service that enables you to consolidate multiple AWS accounts into an organization that you create and centrally manage.
* Paying account should be used for billing purpose only, other Org units accounts can be linked to this paying account for consolidated billing.
* Service Control Policies - Either OrgUnit or individual accounts services can be enabled or disabled
* Tag Policies are a type of policy that can help you standardize tags across resources in your organization's accounts.

## Storage 
### S3 - Simple Storage Service
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

#### Storage Tiers  
* S3 Standard
* S3 One Zone Infrequent Access - low cost, infrequently accessed data and does not require multiple availability zone.
* S3 IA - Infrequently Accessed - data is accessed less frequently but requires rapid access when needed. Low fees than S3 but charged for retrieval fee.
* S3 Intelligent Tiering - data is automatically moved to the most effective access tier.
* S3 Glacier - secure, durable, low cost storage class for data archiving. Retrieval times configurable from minutes to hours.
* S3 Glacier Deep Archive - low cost storage class where the retrieval time of 12 hours is acceptable.

#### Encryption
* Encryption at transit using SSL/TLS
* Encryption at rest 
  * SSE-S3 Server side encryption using AWS managed keys
  * SSE-KMS Server side encryption using keys managed by both AWS and customer
  * SSE-C Server side encryption using customer provided keys
  * Client Side Encryption where client encrypt the file and upload into S3

#### Life-cycle management
Objects can be stored cost effectively though the life cycle management. It is a a set of rules that define actions that S3 applies to a group of objects. For example, you might choose to transition objects to the S3 Standard to IA storage class 30 days after creating them, or archive objects to the S3 Glacier after 90 days.

#### Object Version
* Versioning means keeping multiple variants of an object in the same bucket. 
* Once versioning is enabled it can't be disabled but can be suspended.
* When an object is deleted, s3 insert a delete marker instead of deleting the object.
* We can optionally add another layer of security by configuring a bucket to enable MFA delete
* Object versions can be deleted whenever you want, when you delete the 'delete marker' then the next latest version becomes available.

#### Object Lock
* S3 Object lock stores objects using a WORM (Write Once Read Many) model. It helps prevents objects being delete or modified for a fixed amount of time of indefinitely. 
  * Governance Mode - User can't overwrite or delete object version or alter its lock settings unless they have special permission.
  * Compliance Mode - a protected object can't be overwritten or deleted by any user including the root user.
  * Retention period protect an object version for a fixed amount of time.
  * Legal hold  prevents an object version from being overwritten or deleted. User with S3:PutObjectLegalHold permission can place or remove legal hold on object.
* S3 Glacier Vault Lock allows user to easily deploy and enforce compliance controls for individual S3 Glacier vaults with a Vault Lock policy. 

#### Performance
* You can read 5500 GET request per second per prefix. Better performance can be acheived by spreading your read across different prefixes.
* Use multipart upload for files more than 100 MB (recommended) and required for files more than 5GB
* Download using byte range fetches.

#### Select
* S3 select enables applications to retrieve only a subset of data from an object (csv,json,zip containing csv) by using simple SQL expression.
* Glacier select allows you to run SQL queries against Glacier directly.

#### Cross Account Access
* Using Bucket policies & IAM (applies across the entire bucket) - Programmatic access only
* Using Bucket ACL and IAM (individual objects). Programmatic access only
* Cross account IAM roles. Programmatic and console access.

#### Cross region replication
* Versioning must be enabled on both the source and destination buckets
* Files in an existing bucket are not replicated automatically.
* All subsequent updated files will be replicated automatically.
* Delete markers are not replicated
* Deleting individual version or delete markers will not be replicated.
* Make public action does not get replicated to target bucket.

#### Transfer Acceleration
S3 transfer acceleration utilises the CloudFront edge network to accelerate your uploads to S3. Instead of uploading directly to your s3 bucket, you can use a distinct URL to upload directly to an edge location which will then transfer that file to S3. 

#### Datasync
* Used to move large amounts of data from on-premises to AWS
* Used with NFS and SMB compatible file system
* Replication can be done hourly, daily or weekly
* Install the DataSync agent to start the replication
* Can be used to replicate EFS to EFS
* OnPrem Shared FS <-> AWS DataSync Agent <-> Network Transfers <-> AWS DataSync <-> S3, EFS, FSx 

### Cloud Front
A content delivery network (CDN) is a system of distributed servers that deliver webpages and other web content to a user based on the geographic locations of the user, the origin of the webpage, and a content delivery server.
* Edge location is a location where content will be cache, supports both read and write.
* Origin is the actual location of files that CDN will distribute. This can be an S3, EC2, ELB or RouteR3.
* Distribution is the name given the CDN which consists of a collection of edge location.
* Used to deliver static and dynatic website, streaming and interactive content.
* Request are routed to nearest edge location.
* Web distribution and Real-Time Messaging Protocol (RTMP) media streaming
* Objects are cached for the life of the TTL (time to live)
* You can invalidate cached objects but you will be charged

#### Signed URL or Cookie
* Use signed url/cookie when you want to secure content for authorized users.
* Use CloudFront signed URL for individual files 1 file = 1 url
* Use CloudFront signed Cookie for multiple files 1 cookie = multiple files
* Create signed url/cookie and attach policy which includes url expiration, ip ranges and trusted signers
* Create S3 signed url
  * Issues a request as the IAM user who creates the presigned URL
  * Limited lifetime
* When the origin is EC2 then use CloudFront 
* When the origin is S3 then use S3 presigned URL for single file access.

### Snowball
#### Snowmobile 
Snowmobile is an exabyte-scale data transfer service used to move extremely large amounts of data to AWS. You can transfer upto 100PB per snowmobile, a 45 foot long shipping container. Migrate massive volumes of data to cloud, including video libraries, image repositories, or even a complete data center.

### Storage Gateway
Storage Gateway is a service that connects an on-premises software appliance with cloud based storage to provide seamless and secure integration between an organization's on-premises IT environment and AWS Storage infrastructure.
* File Gateway (NFS & SMB) - Files are stored as objects in your S3 buckets, accessed through a Network File System (NFS)
* Volume Gateway (iSCSI) - Virtual hard disk volumes are stored using the iSCSI block protocol. Data written to these volumes can be synchronously backed up and stored a EBS Snapshots. Snapshots are incremental backups that capture only changed blocks.
  * Stored Volumes - let you store your primary data locally and provides low-latency access to their entire dataset. (eg., think about windows C: drive which contains all OS data)
  * Cached Volumes - let you store only frequently accessed data locally in your storage gateway. (eg., think about windows D: drive which contains user files)
* Tape Gateway (Virtual Tape Library) offers a durable, cost effective solution to archive your data in the AWS Cloud.

### Athena
Athena is an interactive query service which enables you to analyse and query data located in S3 using standard SQL.
* Servers, pay per query per TB scanned
* No need to set up complex ETL process
* Works directly with data stored in S3 (CSV, JSON, log etc)

### Macie
PII (Personally Identifiable Information) eg., name, age, dob, credit card number etc.,
Macie is a security service which uses Machine Learning and NLP to discover, classify and protect sensitive data(PII) stored in S3. Analyse cloud trail logs for suspicious api activity. Includes Dashboards, reports and alerting. Great for PCI-DSS compliance and preventing ID theft.