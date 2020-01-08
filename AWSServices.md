# AWS Services
  - [Compute](#compute)
  - [Storage](#storage)
  - [Database](#database)
  - [Migration](#migration)
  - [Networking and Content Delivery](#networking-and-content-delivery)
  - [Developer Tools](#developer-tools)
  - [Management Tools](#management-tools)
  - [Security, Identity, and Compliance](#security-identity-and-compliance)
  - [Analytics](#analytics)
  - [Artificial Intelligence](#artificial-intelligence)
  - [Mobile Services](#mobile-services)
  - [Application Services](#application-services)
  - [Business Productivity](#business-productivity)
  - [Desktop & App Streaming](#desktop--app-streaming)
  - [Internet of Things](#internet-of-things)
  - [Game Development](#game-development)

## Compute

### EC2 (Elastic Compute Cloud)
EC2 is a web service that provides secure, resizable compute capacity in the cloud.
- **Instance Types**
   - On-Demand Instance
   - Reserved Instance
     - Standard Reserved Instance
     - Convertible Reserved Instance
   - Spot Instance 
   - Dedicated Instance

### ECS (EC2 Container Service)
Amazon EC2 Container Service (ECS) is a highly scalable, high-performance container management service that supports Docker containers.

### ECR (EC2 Container Registry)
Amazon EC2 Container Registry (ECR) is a fully-managed Docker container registry that makes it easy for developers to store, manage, 
and deploy Docker container images.

### Amazon LightSail
Amazon Lightsail is designed to be the easiest way to launch and manage a virtual private server with AWS.

### AWS Batch
AWS Batch enables developers, scientists, and engineers to easily and efficiently run hundreds of thousands of batch computing jobs on AWS.

### AWS Elastic Beanstalk
AWS Elastic Beanstalk is an easy-to-use service for deploying and scaling web applications and
services developed with Java, .NET, PHP, Node.js, Python, Ruby, Go

### AWS Lambda
AWS Lambda is serverless and lets you run code without provisioning or managing servers.

### Auto Scaling
Auto Scaling helps you maintain application availability and allows you to scale your Amazon EC2 capacity up or down automatically 
according to conditions that you define.

## Storage
### Amazon S3 (Simple Storage Service)
AWS S3 is object storage with a simple web service interface to store and retrieve any amount of data from anywhere on the web.
- Storage Classes
  - S3 Standard 
  - S3 Standard Infrequent Access
  - S3 One Zone-Infrequent Access
  - S3 Glacier (S3 Glacier)
  - S3 Glacier Deep Archive

### Amazon EBS (Elastic Block Store)
AWS EBS provides persistent block storage volumes for use with Amazon EC2 instances in the AWS Cloud.

### Amazon EFS (Elastic File System)
Amazon EFS provides simple, scalable file storage for use with Amazon EC2 instances in the AWS Cloud.

### Amazon Glacier 
Amazon Glacier is a secure, durable, and extremely low-cost storage service for data archiving and long-term backup.

### Amazon Storage Gateway
AWS Storage Gateway service seamlessly enables hybrid storage between on-premises storage environments and the AWS Cloud.

## Database
### Amazon RDS (Relational Database Service)
Amazon Relational Database Service (Amazon RDS) makes it easy to set up, operate, and scale a relational database in the cloud.
Amazon RDS provides you six familiar database engines to choose from, including
   - Amazon Aurora is a MySQL and PostgreSQL compatible relational database engine
   - PostgreSQL
   - MySQL
   - MariaDB
   - Oracle
   - Microsoft SQL Server

### Amazon DynamoDB
Amazon DynamoDB is a fast and flexible NoSQL database service for all applications that need consistent, single-digit millisecond latency at any scale.

### Amazon ElastiCache
Amazon ElastiCache is a web service that makes it easy to deploy, operate, and scale an inmemory
cache in the cloud.
  - **Redis** - a fast, open source, in-memory data store and cache
  - **Memcached** - a widely adopted memory object caching system
  
## Migration
### AWS Application Discovery Service
AWS Application Discovery Service helps systems integrators quickly and reliably plan application migration projects by automatically identifying applications running in on-premises data centers, their associated dependencies, and their performance profiles.

### AWS Server Migration Service (SMS) 
AWS Server Migration Service (SMS) is an agentless service which makes it easier and faster for you to migrate thousands of on-premises workloads to AWS.

### AWS Database Migration Service
AWS Database Migration Service helps you migrate databases to AWS easily and securely.

### AWS Snowball 
AWS Snowball is a petabyte-scale data transport solution that uses secure appliances to transfer large amounts of data into and out of AWS.

### AWS Snowball Edge
AWS Snowball Edge is a 100 TB data transfer device with on-board storage and compute capabilities.

### AWS Snowmobile 
AWS Snowmobile is an exabyte-scale data transfer service used to move extremely large amounts of data to AWS. Transfer up to 100 PB per Snowmobile.

## Networking and Content Delivery
### Amazon VPC (Virtual Private Cloud)
Amazon VPC lets you provision a logically isolated section of the AWS Cloud where you can launch AWS resources in a virtual network that you define.

## Amazon CloudFront
Amazon CloudFront is a global content delivery network (CDN) service that accelerates delivery of your websites, APIs, video content, or other web assets.

### AWS Direct Connect
AWS Direct Connect makes it easy to establish a dedicated network connection from your premises to AWS.

### Amazon ELB (Elastic Load Balancing)
Elastic Load Balancing (ELB) automatically distributes incoming application traffic across multiple EC2 instances.
  - Application Load Balancer
  - Network Load Balancer

## Developer Tools
### AWS CodeCommit
AWS CodeCommit is a fully managed source control service that makes it easy for companies to host secure and highly scalable private Git repositories.

### AWS CodeBuild
AWS CodeBuild is a fully managed build service that compiles source code, runs tests, and produces software packages that are ready to deploy.

### AWS CodeDeploy
AWS CodeDeploy is a service that automates code deployments to any instance, including EC2
instances and instances running on premises.

### AWS CodePipeline
AWS CodePipeline is a continuous integration and continuous delivery service for fast and reliable application and infrastructure updates.

### AWS X-Ray 
AWS X-Ray helps developers analyze and debug distributed applications in production or under development, such as those built using a microservices architecture.

## Management Tools
### Amazon CloudWatch 
Amazon CloudWatch is a monitoring service for AWS Cloud resources and the applications you run on AWS.

### Amazon EC2 Systems Manager
Amazon EC2 Systems Manager is a management service that helps you automatically collect software inventory, apply operating system (OS) patches, create system images, and configure Windows and Linux operating systems.

### AWS CloudFormation
AWS CloudFormation gives developers and systems administrators an easy way to create and manage a collection of related AWS resources.

### AWS CloudTrail
AWS CloudTrail is a web service that records AWS API calls for your account and delivers log files to you.

### AWS Config 
AWS Config is a fully managed service that provides you with an AWS resource inventory, configuration history, and configuration change notifications to enable security and governance.

### AWS OpsWorks
AWS OpsWorks is a configuration management service that uses Chef, an automation platform that treats server configurations as code.

### AWS Service Catalog
AWS Service Catalog allows organizations to create and manage catalogs of IT services that are approved for use on AWS.

### AWS Trusted Advisor 
AWS Trusted Advisor is an online resource to help you reduce cost, increase performance, and improve security by optimizing your AWS environment.

### AWS Personal Health Dashboard
AWS Personal Health Dashboard provides alerts and remediation guidance when AWS is experiencing events that might affect you.

### AWS Managed Services
AWS Managed Services provides ongoing management of your AWS infrastructure so you can focus on your applications.

## Security, Identity, and Compliance
### Amazon Cloud Directory
Amazon Cloud Directory enables you to build flexible, cloud-native directories for organizing hierarchies of data along multiple dimensions.

### AWS IAM (Identity and Access Management) 
AWS IAM enables you to securely control access to AWS services and resources for your users.

### Amazon Inspector 
Amazon Inspector is an automated security assessment service that helps improve the security and compliance of applications deployed on AWS.

### AWS Certificate Manager
AWS Certificate Manager is a service that lets you easily provision, manage, and deploy Secure Sockets Layer/Transport Layer Security (SSL/TLS) certificates for use with AWS services.

### AWS CloudHSM
AWS CloudHSM service helps you meet corporate, contractual, and regulatory compliance requirements for data security by using dedicated Hardware Security Module (HSM) appliances within the AWS Cloud.

### AWS Directory Servic
AWS Directory Service for Microsoft Active Directory (Enterprise Edition), also known as AWS Microsoft AD, enables your directory-aware workloads and AWS resources to use managed Active Directory in the AWS Cloud.

### AWS KMS (Key Management Service)
AWS Key Management Service (KMS) is a managed service that makes it easy for you to create and control the encryption keys used to encrypt your data.

### AWS Organizations
AWS Organizations allows you to create groups of AWS accounts that you can use to more easily manage security and automation settings.

### AWS Shield
AWS Shield is a managed Distributed Denial of Service (DDoS) protection service that safeguards web applications running on AWS. 
  - Standard Shield, free for all users
  - Advanced Shield, is a paid service 

### AWS WAF
AWS WAF is a web application firewall that helps protect your web applications from common web exploits that could affect application availability, compromise security, or consume excessive resources.

## Analytics
### Amazon Athena
Amazon Athena is an interactive query service that makes it easy to analyze data in Amazon S3 using standard SQL. Athena is serverless, so there is no infrastructure to manage.

### Amazon EMR
Amazon EMR provides a managed Hadoop framework that makes it easy, fast, and costeffective to process vast amounts of data across dynamically scalable EC2 instances.

### Amazon CloudSearch
Amazon CloudSearch is a managed service in the AWS Cloud that makes it simple and costeffective to set up, manage, and scale a search solution for your website or application.

### Amazon Elasticsearch
Amazon Elasticsearch Service makes it easy to deploy, operate, and scale Elasticsearch for log analytics, full text search, application monitoring, and more.

### Amazon Kinesis
Amazon Kinesis is a platform for streaming data on AWS, offering powerful services to make it easy to load and analyze streaming data, and also providing the ability for you to build custom streaming data applications for specialized needs.
  - **Amazon Kinesis Firehose** is the easiest way to load streaming data into AWS
  - **Amazon Kinesis Analytics** is the easiest way to process streaming data in real time with standard SQL
  - **Amazon Kinesis Streams** enables you to build custom applications that process or analyze streaming data for specialized needs

### Amazon Redshift
Amazon Redshift is a fast, fully managed, petabyte-scale data warehouse that makes it simple and cost-effective to analyze all your data using your existing business intelligence tools.

### Amazon QuickSight
Amazon QuickSight is a fast, cloud-powered business analytics service that makes it easy to build visualizations, perform ad-hoc analysis, and quickly get business insights from your data.

### AWS Data Pipeline
AWS Data Pipeline is a web service that helps you reliably process and move data between different AWS compute and storage services, as well as on-premises data sources, at specified intervals.

### AWS Glue
AWS Glue is a fully managed ETL service that makes it easy to move data between your data stores.

## Artificial Intelligence
### Amazon Lex
Amazon Lex is a service for building conversational interfaces into any application using voice
and text.

### Amazon Polly
Amazon Polly is a service that turns text into lifelike speech.

### Amazon Rekognition
Amazon Rekognition is a service that makes it easy to add image analysis to your applications.

### Amazon ML (Machine Learning)
Amazon Machine Learning is a service that makes it easy for developers of all skill levels to use machine learning technology.

## Mobile Services
### AWS Mobile Hub 
AWS Mobile Hub provides an integrated console experience that you can use to quickly create and configure powerful mobile app backend features and integrate them into your mobile app.

### Amazon Cognito
Amazon Cognito lets you easily add user sign-up and sign-in to your mobile and web apps.

### Amazon Pinpoint
Amazon Pinpoint makes it easy to run targeted campaigns to drive user engagement in mobile apps.

### AWS Device Farm
AWS Device Farm is an app testing service that lets you test and interact with your Android, iOS, and web apps on many devices at once, or reproduce issues on a device in real time.

### AWS Mobile SDK
The AWS Mobile SDK helps you build high quality mobile apps quickly and easily.

### Amazon Mobile Analytics
With Amazon Mobile Analytics, you can measure app usage and app revenue.

## Application Services
### AWS Step Functions
AWS Step Functions makes it easy to coordinate the components of distributed applications and microservices using visual workflows

### Amazon API Gateway
Amazon API Gateway is a fully managed service that makes it easy for developers to create, publish, maintain, monitor, and secure APIs at any scale.

### Amazon Elastic Transcoder
Amazon Elastic Transcoder is media transcoding in the cloud.

### Amazon Simple Workflow
Amazon Simple Workflow (Amazon SWF) helps developers build, run, and scale background jobs that have parallel or sequential steps.

## Messaging
### Amazon SQS (Amazon Simple Queue Service)
Amazon SQS is a fast, reliable, scalable, fully managed message queuing service.

### Amazon SNS (Simple Notification Service)
Amazon Simple Notification Service (Amazon SNS) is a fast, flexible, fully managed push notification service that lets you send individual messages or to fan-out messages to large numbers of recipients.

### Amazon SES (Simple Email Service)
Amazon SES is a cost-effective email service built on the reliable and scalable infrastructure that Amazon.com developed to serve its own customer base.

## Business Productivity
### Amazon WorkDocs
Amazon WorkDocs is a fully managed, secure enterprise storage and sharing service with strong administrative controls and feedback capabilities that improve user productivity.

### Amazon WorkMail
Amazon WorkMail is a secure, managed business email and calendar service with support for existing desktop and mobile email client applications.

### Amazon Chime
Amazon Chime is a communications service that transforms online meetings with a secure, easy-to-use application that you can trust.

## Desktop & App Streaming
### Amazon WorkSpaces
Amazon WorkSpaces is a fully managed, secure desktop computing service that runs on the AWS Cloud.

### Amazon AppStream 2.0
Amazon AppStream 2.0 is a fully managed, secure application streaming service that allows you to stream desktop applications from AWS to any device running a web browser, without rewriting them.

## Internet of Things
### AWS IoT
AWS IoT is a managed cloud platform that lets connected devices easily and securely interact with cloud applications and other devices.

### AWS Greengrass
AWS Greengrass is software that lets you run local compute, messaging, and data caching for connected devices in a secure way.

### AWS IoT Button
AWS IoT Button is a programmable button based on the Amazon Dash Button hardware.

## Game Development
### Amazon GameLift
Amazon GameLift is a managed service for deploying, operating, and scaling dedicated game servers for session-based multiplayer games.

## Amazon Lumberyard 
Amazon Lumberyard is a free, cross-platform, 3D game engine for you to create the highestquality games, connect your games to the vast compute and storage of the AWS Cloud, and engage fans on Twitch.


