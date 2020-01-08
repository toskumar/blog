# AWS Services
  - [Compute](#compute)
  - [Storage](#storage)
  - [Database](#database)
  - [Migration](#migration)
  - [Network and Content Delivery](#network-and-content-delivery)
  - [Developer Tools](#developer-tools)

## Compute

### EC2 (Elastic Compute Cloud)
EC2 is a web service that provides secure, resizable compute capacity in the cloud.
- **Instance Types**
   - On-Demand Instance
   - Reserved Instance
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






