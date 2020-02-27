# Amazon Web Services (AWS)

- Infrastructure as a service (IaaS)
- Software as a service (SaaS)
- Platform as a service (Paas)

## Products

- Amazon EC2
- Amazon RDS
- AWS Direct Connect
- Amazon EBS
- Amazon S3
- Elastic Load Balancing
- Amazon Route 53
- Amazon VPC
- Elastic IP

## Background

- pay as you go model
- scales up as much as you need
- data centers are available all around the world in availability zones (AZ)
- can securely store data
- run web application servers
- send bulk emails
- store information in databases (MySQL, SQL, Oracle, PostgreSQL)

## Compute

- Elastic Compute Cloud (EC2)
- virtual machine
- LightSail for automatic deployment and managing compute, storage and networking
- Lambda: AWS serverless technology where functions can be run only when you need them, thereby saving money
- Batch: can run batch computing workloads
- Elastic Beanstalk: automated provisioning and deployment of resources

## Storage

- Simple Storage Service (S3): store different objects such as files, images, documents, folders, basically assets
- Elastic File System (EFS): provides file storage to the user
- Glacier: archival service to store files for extended periods of time
- Storage Gateway: virtual machine for data backup

## Databases

- Relational Database Service (RDS)
  - can run MySQL, PostgreSQL, Oracle, MariaDB or SQL Server
- DynamoDB
  - NoSQL databases
- Elasticache
  - can cache data that is most frequently queried, effectively reducing the server load
- Neptune
  - scalable database service for graphs
- RedShift
  - data warehousing solution for running complex OLAP queries

## Migration

- Data Migration Service (DMS)
  - provides service to migrate to AWS from custom database solutions
- Server Migration Service (SMS)
  - can migrate to AWS
- Snowball

## Networking & Content Delivery

- Virtual Private Cloud (VPC)
  - can deploy all resources and secure them
- CloudFront
  - content delivery network (CDN)
  - cache resources based on location
- Route53
  - Domain Name Service (DNS) for AWS
  - used for registring domain names
- Direct Connect
  - connecting data center availability zones
- API Gateway
  - creating, storing and managing APIs

## Developer Tools

- CodeStar: create, manage and work with software development projects
- CodeCommit: version control service
- CodeBuild: code automation & code compilation
- CodeDeploy: deploy code in EC2 instances
- CodePipeline: keep track of all steps such as testing, building, authentication, deployment, etc.
- Cloud9: Integrated Development Environment (IDE)
- X-Ray: application behavior analysis

## Management Tools

- AWS CloudWatch: monitor environments such as CPU
- CloudFormation: turning infrastructure into the cloud
- CloudTrail: AWS resource auditing
- OpsWorks: automating Chef deployments on AWS
- Config: monitoring environment, and providing alerts when a configuration is broken
- Service Catalog: gives enterprise customers the ability to select what services they wish to utilize
- Trusted Advisor: provides recommendations and optimizations to help save money
- AWS Auto Scaling: will automatically scale resources based on the CloudWatch metrics
- System Manager: provides tools to group resources for quick insights and to help identify potential issues
- Managed Services: provides ongoing management of AWS infrastructure

## Analytics

- Athena: run SQL queries on S3 buckets
- Elastic Map Reduce: big data processing like Apache Spark, Hadoop or Splunk
- CloudSearch: managed search engine for web application
- ElasticSearch: application monitoring
- Kinesis: streaming and analysis of real-time data, can be scaled up to massive amounts
- Data Pipeline: move data from one place to another
- QuickSight: business analytics tool for rich visualizations from databases
- Glue: data categorization, cleaning and transport from one store to another

## Security, Identity and Compliance

- Identity and Access Management (IAM)
- Inspector: identifies security vulnerabilities
- Certificate Manager for SSL cert
- DirectoryService: logging into AWS from company's account
- Web Application Firewall (WAF): provides account level protection from SQL injection and XSS
- CloudHSM: compliance via hardware security module (HSM)
- CloudDirectory: provides tools to build flexible cloud-based directories for organizing data hierarchies along with dimensions
- Key Management Services: create or control encryption keys used for data encryption
- Organizations: creates groups of accounts for security and automation
- Shield: DDoS protection service
- Artifact: provides compliance certifications
- Macie: classify and protect sensitive and business content
- Guard Duty: intelligent threat detection to protect AWS accounts and workloads

## Application Services

- Step Functions: visualization of processes inside application and microservices
- Simple Workflow Service: coordination of automated and human-led tasks
- Simple Notifications Service: sends notifications via email or SMS
- Simple Queue Service: decouples applications
- Elastic Transcoder: provides video transcoding

## Mobile Services

- Mobile Hub: adding, designing and configuring features into a mobile app
- Cognito: user signup
- Device Farm: improving app quality by quickly testing hundreds of mobile devices
- AWS AppSync: fully managed GraphQL service with offline programming features and real-time data synchronization
- Mobile Analytics: analyzes mobile data effectively

## Business Productivity

- Alexa for Business
- Chime: online meeting and video conferencing
- WorkDocks: document management
- WorkMail: emails

## Desktop

- WorkSpaces: remote desktop
- AppStream: streaming desktop applications

## Artificial Intelligence

- LEX: chatbot authoring
- Recognition: face-recognition serivce
- Machine Learning: ML models and algorithms
- Polly: text-to-speech service
- SageMaker: build, train and deploy ML models
- Comprehend: natural processing language
- Transcribe: speech to text service
- Translate: converts text from one language to another

## AR & VR

- Sumerian: tools to author AR/VR experiences

## Customer Engagement

- Amazon Connect: customer care center
- Pinpoint: user analystics
- Simple Email Service (SES): send bulk emails

## Game Development

- GameLift: host dedicated game servers

## IoT

- IoT Core: provides service for devices to connect securely
- IoT Device Management: manages various devices that are connected to each other
- Greengrass: allows devices to process locally generated data
- Amazon FreeRTOS: real-time OS for microcontrollers to securely connect devices locally or in the cloud

---

- *NOTE: Much of the material above was copied from the article in source1, I give full credit to Asha Goyal, the author of source1's article*
- [source1](https://blog.bitsrc.io/the-amazing-world-of-amazon-web-services-aws-edc34614041a)
