# Implementation and Operation

* Type of deployments
  * Big Bang - use this deployment when we can't run both the systems at the same time
  * Phased Rollout - Gradually deploy new system and decommission the old system
  * Parallel Adoption - Run old and new system run simultaneously sometimes risk is higher

* Rolling deployment - Multiple version in production at the same time.
* Canary deployment - Have current and new version deployed and route some percent of traffic to new version to analyse performance
  * A/B testing - Deploy a new version into production and configure a set of amount of new inbound traffic to use the new (B) version record flow-on data about the outcome of those to used the new version

* Continuous Integration - Merge code changes back to main branch as frequently as possible.
* Continuous Delivery - You have automated your release process to the point you can deploy at the click of a button.
* Continuous Deployment - Each code changes that passes all stages of the release process is released to production with no human intervention required.

* AI Services
  * Amazon Comprehend - NLP service that finds insight and relationships within text. Sentiment analysis of social media post
  * Amazon Forecast - Combines time series data with other variables to deliver highly accurate forecasts. Forecast seasonal demand for a specific color of shirt.
  * Amazon Lex - Build conversational interfaces that can understand that intent and context of natural speech. Create a customer service chatbot to automatically handle routine requests.
  * Amazon Personalize - Recommendation engine as a service based on demographic and behavioral data. Provide potential upsell products at checkout during a web transaction.
  * Amazon Polly - Text-to-Speach service supporting multiple languages, accents and voices. Provide dynamically generated personalized voice response for inbound callers.
  * Amazon Rekognition - Image and video analysis to parse and recognize objects, people, activities and facial expressions. Provide an additional form of employee authentication through facial recognition as they scan an access badge.
  * Amazon Textract - Extract text, context and metadata from scanned documents. Automatically digitize and process physical paper forms.
  * Amazon Transcribe - Speech-to-text as a service. Automatically create transcripts of recorded presentations.
  * Amazon Translate - Translate text to and from many different languages.Dyanmically create localized web content for users based on their geography.

### Amazon SageMaker Deployment
* Offline usage - Asynchronous or Batch. Generate prediction for a whole set of data all at once. Sage Maker Batch Transform. 
* Online usage - Synchronous or Realtime. Generate low letency prediction. SageMaker hosting services.
* SageMaker hosting services
  * Create a Model - this is the inference engine that will provide predictions for your endpoint.
  * Create an endpoint configuration - Defines the model to use, inference instance type, instance count, variant name and weight also called a production variant.
  * Create an endpoint - Publishes the model via the endpoint configuration to be called by the SageMaker api InvokeEndpoint() method

* Inference Pipelines - A SageMaker model composed of a sequence of two or five containers which can process data as a flow. These can be build-in algorithms or your own custom algorithms in docker containers.

* SageMaker Neo : Enables a simplified way to optimize machine learning models for a variety of computing architectures such as ARM, Intel and nVidia processors. Consists of a compiler to convert the machine learning model into an optimized binary and a runtime to execute the model on the target architecture.
* Elastic Inference : Speeds up throughput and decreases latency of real time inferences deployed on SageMaker hosted services using only cpu-based instances but much more cost-effective than a full GPU instance. Must be configured when you create a deployable model and EI is not available for all algorithms yet.
 
### Other ML Deployment
* ECS
* EC2
* Amazon Elastic Map reduce
* On-Premises 

* Security
  * Use VPC, NACL, SG, IAM, KMS to secure Amazon ML and SageMaker resources
  * Use VPC Endpoint to increase security
  * Notebook instances are Internet enabled by default but can be disabled

* Monitor and Evaluate
  * Cloud Watch is integrated with SageMaker for monitoring
  * CloudWatch has limited storage while CloudTrail has unlimited storage if you log into an S3 bucket.
