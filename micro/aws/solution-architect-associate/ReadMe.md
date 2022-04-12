# AWS Solution Architect Associate

## IAM
### IAM Roles
* Roles are more secure than storing your access key and secret access key on individual EC2 instances
* Roles are easier to manage
* Roles can be assigned to an EC2 instance after it is created using both the console and command line.
* Roles are universal, you can use them in any region

### IAM Policies

Amazon Resource Name (ARN)
ARN all begin with - arn:parition:service:region:account_id:
eg., arn:aws:s3:us-east-1:123456789
and ends with 
resource, resource_type/resource, resource_type/resource:qualifier

Policy
* JSON document that deines permissions
* Identity policy
* Resource policy
* No effect until attached
* List of statements

```json
{
  "Version": "2012-10-10",
	"Statement": [
	  {
		  "Sid": "SpecificTable",
			"Effect": "Allow",
			"Action": [
				"dynamodb:BatchGet*",
				"dynamodb:Get*",
				"dynamodb:Query",
				"dynamodb:Scan"
			],
			"Resource": "arn:aws:dynamodb:*:*:table/MyTable"
		}
	]
}
```
Exam Tips
* Not explicitly allowed == implicityly denied
* Explicit deny > everthing else
* Only attached policies have effect
* AWS joins all applicable policies
* AWS managed VS customer managed

### Permission Boundaries
* Used to delegate administration to other users
* Prevent priviledge escalation or unnecessarily broad permission
* Control maximum permission an IAM  policy can grant
* Use cases:
  * Developers creating roles for Lambda functions
	* Application owners creating roles for EC2 instances
	* Admins creating adhoc users
	
### AWS Resource Access Manager (RAM)
Resource Access Manager allows __resource sharing__ between accounts

### AWS Single Sign-On
SSO service helps centrally manage access to AWS accounts and business applications. SAML 2.0 enabled application can use SSO to login.

### AWS Organization
AWS Organization is an account management service that enables you to consolidate multiple AWS accounts into an organization that you create and centrally manage.
* Paying account should be used for billing purpose only, other Org units accounts can be linked to this paying account for consolidated billing.
* Service Control Policies - Either OrgUnit or individual accounts services can be enabled or disabled
* Tag Policies are a type of policy that can help you standardize tags across resources in your organization's accounts.

## AWS Directory Service
* Family of managed services
* Connect AWS resources with on-premises AD
* Standalone directory in the cloud
* Use existing corporate credentials
* SSO to any domain-joined EC2 instance

### Active Directory
* On-premises directory services
* Hierarchical database of users, groups, computers - trees and forests
* Group policies
* LDAP and DNS
* Kerberos, LDAP and NTML authentication
* Highly available

### Managed Microsoft AD
* AD domain controller (DC) running Windows Server
* Reachable by applications in your VPC
* Add DCs for HA and performance
* Exclusive access to DC's
* Extend existing AD to on-premises using AD Trust

### Simple AD
* Standalone managed directory
* Basic AD features
* Small <=500 and Large <=5000 users
* Easier to manage EC2
* Linux workloads that need LDAP
* Does not support trusts (can't join on-premises AD)

### AD Connector
* Directory gateway (proxy) for on-premises AD
* Avoid caching information in the cloud
* Allow on-premises users to log in to AWS using AD
* Join EC2 instances to your existing AD domain
* Scale across multiple AD connectors

### Cloud Directory
* Directory-based store for developers
* Multiple hierarchies with hundreds of million of objects
* Use cases: org charts, course catalogs, device registries
* Fully managed service

### Cognito User Pools
* Managed user directory for SaaS applications
* Sign-up and sign-in for web or mobile
* Works with social media identities
 


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

#### EFS - FSx 
* EFS - When you need distributed, highly resilient storage for Linux instances and Linux-based applications

* Amazon FSx for windows - When you need centralized storage for Windows based applications such as Share point, Microsoft SQL Server, Workspaces, IIS Web Server or any other native Microsoft Application.

* Amazon FSx for Lustre - When you need high speed, high capacity distributed storage. This will be for applications that do High Performance Compute(HPC), financial modelling etc. Remember that FSx for Lustre can store data directly on S3

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

### Elastic File System (EFS)
EFS is a file storage service for EC2 instances. EFS is easy to use and provides a simple interface that allows you to create and configure file systems quickly and easily.

```sh
$ yum install -y amazon-efs-utils

$ mount -t efs -o tls <fs-name>:/ <local-mount-path>
```

## Analytics
### Athena
Athena is an interactive query service which enables you to analyse and query data located in S3 using standard SQL.
* Servers, pay per query per TB scanned
* No need to set up complex ETL process
* Works directly with data stored in S3 (CSV, JSON, log etc)

### Macie
PII (Personally Identifiable Information) eg., name, age, dob, credit card number etc.,
Macie is a security service which uses Machine Learning and NLP to discover, classify and protect sensitive data(PII) stored in S3. Analyse cloud trail logs for suspicious api activity. Includes Dashboards, reports and alerting. Great for PCI-DSS compliance and preventing ID theft.

## Compute
### EC2 Elastic Compute Cloud
EC2 is a web service that provides resizable compute capacity in the cloud. EC2 reduce time required to boot the new server instances in minutes, scale both up and down as the computing requirements change.
* On Demand - instance allows you to pay a fixed rate by the hour or second with no commitments.
* Reserved - instance provides you with a capacity reservation and offers a significant discount on the hourly charge. Contract terms are 1 to 3 years.
  * Standard reserved instance offers upto 75% off on demand instances. The more you pay up front and the longer the contract, the greater the discount.
  * Convertible reserved instance offers upto 54% on demand, capability to exchange RI of equal or greater value.
  * Scheduled reserved instance is available to launch within the time windows you reserve. This options allows you to match your capacity reservation to a predictable recurring schedule that only requires a fraction of a day, a week or a month.  
* Spot - instance enables you to bid whatever price you want for instance capacity  with flexible start and end times. 
  * Spot block can be used to stop your spot instances from being terminated even if the spot price goes over your max spot price. You can set spot blocks for between one to six hours currently.
* Dedicated Hosts - physical EC2 server dedicated to use your existing server bound software licenses.

### EC2 Instance Types
* F - FPGA
* I - IOPS
* G - Graphics
* H - High disk throughput
* T - Cheap general purpose 
* D - Density
* R - RAM
* M - Main choice for general pupose apps
* C - Compute
* P - Graphics (think Pics)
* X - Extreme memory
* Z - Extreme memory and CPU
* A - Arm based workloads
* U - Bare metal

### EC2 FAQ
* Termination Protection is turned off by default, you must turn it on.
* On an EBS backed instance, the default action is for the root EBS volume to be deleted when the instance is terminated.
* EBS Root volumes of your default AMI's CAN be encrypted. You can also use a third party tool (such as bit locker) to encrypt the root volume, or this can be done when creating AMI's in the AWS console or using the API.
* Additional volumes can be encrypted

### Security Groups
* All inbound traffic is blocked by default
* All outbound traffic is allowed
* Changes to security groups take effect immediately
* You can have any number of EC2 instances within a security group
* You can have multiple security groups attached to EC2 instances
* Security groups are Stateful. when you create an inbound rule allowing traffic in, that traffic is automatically allowed back out again.
* You cannot block specific IP addresses using Security Groups, instead use Network Access Control Lists.
* You can specify allow rules but not deny rules

### Elastic Block Store (EBS)
EBS provides persistent block storage volumes for use with EC2 instances. Each EBS volume is automatically replicated within its availability zone to protect you from component failure, offering high availability and durability.
* Types of EBS Storage
  * General purpose (SSD) - Most work loads
  * Provisioned IOPS (SSD) - Database
  * Throughput optimised hard disk drive - Big data and data warehouses 
  * Cold hard disk drive - File servers
  * Magnetic - Workloads where data is infrequently accessed

### EBS Snapshots
* Volumes exists on EBS and think EBS as a virtual hard disk
* Snapshots exits on S3 and think of snapshots as a photograph of the disk
* Snapshots are point in time copies of volumnes
* Snapshots are incremental - this means that only the blocks that have changed since your last snapshot are moved to S3
* To create a snapshot for EBS volumes that serve as root devices, you should stop the instance before taking the snapshot. However you can take a snap while the instance is running.
* You can create AMI from snapshots
* You can change EBS volume sizes on the fly, including changing the size and storage type.
* Volumes will always be in the same availability zone as the EC2 instance.
* To move an EC2 volume you can one AZ to another, take a snapshot of it, create an AMI from the snapshot and then use the AMI to launch the EC2 instance in a new AZ
* To move an EC2 volume from one region to another, take a snapshot of it, create an AMI from the snapshot and then copy the AMI from one region to the other. Then use the copied AMI to launch the new EC2 instance in the new region.

### Encrypted root device volumes & snapshots
* Snapshots of encrypted volumes are encrypted automatically
* Volumes restored from encrypted snapshots are encrypted automatically
* You can share snapshots only if they are unencrypted
* Unencrypted snapshots can be shared with other AWS accounts or made public
* You can now encrypt root device volumes upon creation of the EC2 instance
Steps to convert an unencrypted volume to encrypted volume
* Create a snapshot of the unencrypted root device volume
* Create a copy of the snapshot and select the encrypt option
* Create an AMI from the encrypted snapshot
* Use that AMI to launch new encrypted instances 

### AMI Types
All AMI are categorized as either backed by Amazon EBS or backed by instance store.
* EBS Volumes - The root device for an instance launched from the AMI is an amazon EBS volume created from an EBS snapshot.
* Instance store volumes - The root device for an instance launched from the AMI is an instance store volume created from a template stored in S3.
  * Instance store volumes are sometimes called ephemeral storage
  * Instance store volumes cannot be stopped. If the underlying host fails, you will lose your data
  * EBS backed instances can be stopped. you will not lose the data on this instance if it is stopped.
  * You can reboot both, you will not lose your data
  * By default both root volumes will be deleted on termination. However with EBS volumes you can tell AWS to keep the root device volume.

### ENI vs EN vs EFA
* ENI - Elastic network interface - essentially a virtual network card. 
  * For basic networking. Perhaps you need a separate management network to you production network or a separate logging network and you need to do this at low cost. In this scenario use multiple ENIs for each network.
* EN - Enhanced networking. uses single root IO virtualization (SR-IOV) to provide high-performance networking capabilities on supported instance types.
  * When you need speeds between 10Gbps and 1000Gbps. Anywhere you need reliable, high throughput.
* Elastic Fabric Adapter - A network device that you can attach to your EC2 instance to accelerate High Performance Computing (HPC) and machine learning applications.
  * When you need to accelerate High Performance Computing (HPC) and machine learning applications or if you need to do an OS by-pass. If you see a scenario question mentioning HPC or ML then choose EFA

### Placement Groups
* Cluster placement group is a grouping of instances within a single Availability Zone. Placement groups are recommended for applications that need low network latency, high network throughput or both.

* Spread placement group is a group of instance that are each placed on distinct underlying hardware. Recommended for applications that have a small number of critical instances that should be kept separate from each other.

* Partition placement groups divides each group into logical segments called partitions. EC2 ensures that each partition within a placement group has its own set of racks. Each rack has its own network and power source. No two partitions within a placement group share the same racks, allowing you to isolate the impact of hardware failure within your application.

## Monitoring
### Cloud Watch
* Cloud Watch is used for monitoring performance
* Cloud Watch can monitor most of AWS as well as your applications that run on AWS
* Cloud Watch with EC2 will monitor events every 5 minutes by default
* You can have 1 minute intervals by turning on detailed monitoring
* You can create CloudWatch alarms which trigger notifications

## Security
### Web Application Firewall (WAF)
WAF is a web application firewall that lets you monitor the HTTP and HTTPS requests that are forwarded to Amazon CloudFront an Application Load Balancer or API Gateway

You can configure conditions such as what IP addresses are allowed to make this request or what query string parameters need to be passed for that request to be allowed. Then the application load balancer or CloudFront or API Gateway will either allow this content to be received or to give a HTTP 403 Status Code.
Behaviors and Protection 
* Allow all requests except the ones you specify
* Block all requests except the ones you specify
* Count the requests that match the properties you specify
* IP addresses that requests originates
* Country that requests orginate
* Values in request headers
* Strings that appears in requests, either specific strings or string that match regular expression (regex) patterns
* Length of requests
* Presence of SQL code that is likely to be malicious (known as SQL injection)
* Presence of a script that is likely to be malicious (known as cross-site scripting)

## Utility
### Command Line
Download EC2 key pair to connect EC2 instance and launch ssh console

```sh
# login as ec2-user
$ ssh ec2-user@<IP ADDERSS> -i <public_key>

# change to super user
$ sudo su

# configure aws by providing access key, secret and default region, 
# This command saves the credentials in the userhome/.aws directory.
# For security reason this is not advisable to connect EC2 using command line credentials.
$ aws configure

# list all s3 bucket names
$ aws s3 ls
```

Now create an administrator role for EC2 service and attach the role to the EC2 instance.

```sh
# login as ec2-user
$ ssh ec2-user@<IP ADDERSS> -i <public_key>

# change to super user
$ sudo su

# change to home directory and delete .aws directory
$ cd ~ | rm -rf .aws

# list all s3 bucket names
$ aws s3 ls
```

### Boot script

```sh
#!/bin/bash
yum update -y
yum install httpd -y
service httpd start
chkconfig httpd on
cd /var/www/html
echo "<html><h1>Hello AWS Cloud, Welcome to my web page</h1></html>" > index.html
```

### Instance Metadata
Used to get information about an instance such as public ip address

```sh
# login as ec2-user
$ ssh ec2-user@<IP ADDERSS> -i <public_key>

# change to super user
$ sudo su

# display the user bootstrap command
$ curl http://<ip.address>/latest/user-data

# list of sub commands for meta-data
$ curl http://<ip.address>/latest/meta-data

# meta-data command to get public-ipv4 of the ec2 instance
$ curl http://<ip.address>/latest/meta-data/public-ipv4
```

## AWS Database
### Relational Database Service (RDS)
* SQL Server
* Oracle
* MySQL Server
* PostgreSQL
* Aurora
* MariaDB
RDS has two key feature
* Multi AZ for disaster recovery
* Read Replicas for performance

Remember the followings points
* RDS run on virtual machines and its a managed service so we can't login in and patch operating system
* RDS is NOT Serverless however Aurora is Serverless
* RDS has two different types of Backups and Automated Backups and Database Snapshots
Read Relicas
* Can be Multi-AZ
* Used to increase performance
* Must have backups turned on
* Can be in different regions
* Can be Aurora, MySQL, PostgreSQL, MariaDB, Oracle and SQL Server
* Can be promoted to master, this will break the read replica
Multi-AZ
* Used for DR
* You can force failover from one AZ to another by rebooting the RDS instance.
Encryption - at reset is supported by SQL Server, Oracle, MySQL, PostgreSQL, MariaDB and Aurora. Encryption is done using the AWS Key Management Service (KMS). Once your RDS instance is encrypted, the data stored at rest in the underlying storage is encrypted, as are its automated backups, read replicas and snapshots.

Aurora
* 2 copies of your data are contained in each AZ, with minimum of 3 availability zones. 6 copies of your data.
* Can share Aurora snapshots with other AWS Accounts
* 3 types of replicas available. Aurora replicas, MySQL replicas & PostgreSQL replicas. Automated failover is only available with Aurora replicas.
* Aurora has automated backups turned on by default. You can also take snapshots with Aurora, You can share these snapshots with other AWS accounts.
* Use Aurora Serverless if you want a simple, cost-effective option for infrequent, intermittent or unpredictable workloads

### Non Relational Databases 
DynamoDB (No SQL)
* Stored on SSD storage
* Spread across 3 geographically distinct data centers
* By default supports eventual consistent reads 
* Strongly consistent reads
Comparison 
* Collection - Table
* Document - Row
* key value - Column

OnLine Transaction Processing OLTP  - RDS
OnLine Analytical Processing OLAP - RedShift

RedShift - Data Warehousing databases use different type of architecture both from a database perspective and infrastructure layer. 
Backups
* Enabled by default with a 1 day retention period
* Maximum retention period is 35 days
* Redshift always attempts to maintain at least three copies of your data (the original and replica on the compute nodes and a backup in Amazon S3)
* Redshift can also asynchronously replicate your snapshots to S3 in another region for disaster recovery.
 
Elastic Cache
Elastic Cache is a web service that makes it easy to deploy, operate, and scale an in-memory cache in cloud. Increase database and web application performance.
* MemCached - Simple to use and scales horizontally.
* Redis - Supports Multi-AZ, backup, restores and scales horizontally. 

