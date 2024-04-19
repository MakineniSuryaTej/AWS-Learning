# AWS-Learning-Progress

## Day 1:

> Introduction
- What's a cloud? A collection of services (databases, virtual servers, etc) that creates a platform.
- The AWS has pay-as-you-go pricing.
- AWS Services

> Security and Identity
- AWS Identity Access Management (IAM), AWS Secrets Manager protects the secrets required, and Directory Service provides the directories for the org with specific users.
- IAM Practice Lab
1. For this lab there is an AWS account, inside of IAM there are different groups such as Admin, Developers, and Test. Each group has a certain set of permissions.
2. Three users have already been created and we can check them in the **Users Tab**, three groups were created previously named EC2-Admin, EC2-Support, and S3-Support which can be seen under **User groups Tab**.
3. The EC2-Admin has an inline policy (has permissions to describe, start, and stop EC2 instances | also a few metrics). The EC2-Support group has managed policy (has permissions to describe EC2 instances and list cloud metrics). The S3-Support has managed policy (has permissions of read-only access such as get, list, and describe objects.)
4. So now we have 3 users (U1, U2, U3) and we are going to assign these users to the above groups. First, assign the U1 to the S3-Support group (**Process: Click on the S3-Support group, click the Add Users button, select the U1, and then click on Add Users**). Then we are going to do the same for the U2 and U3. Add the U2 to the EC2-Support group and the U3 to the EC2-Admin group.
5. We can edit the permissions of any user (**Process: Click on the user, under the permissions tab expand the policy, and click on the edit**).
6. To demonstrate these permissions, **go to the dashboard copy the sign-in URL paste it into a new tab, and log in as U1. To check permissions click on S3 and click on create bucket, it fails since U1 does not have permissions and this goes the same with EC2 since U1 has read-only permissions**.
7. Similarly we log in as U2, here when we click on EC2 and click on instances it works and has more permissions than U1, but when we try to stop that instance it fails. U2 also cannot create or view the buckets.
8. log in as U3, head over to EC2, and if we try to stop the instance it stops since U3 is in the group EC2-Admin. 

## Day 2:

> Elastic Compute Cloud (EC2)
- It is a service that allows to rent virtual computers (option to choose various specifications). Everything is an instance. For example, a task that takes 24 hours can be broken down into 24 1-hour instances, which by the same cost but more efficiency.

> Containers
- The purpose of a container is to create a package of your program and all of its library and dependencies it uses, to produce an image that can be able to run any computer.

> Lambda
- It is a serverless computing service that runs your code in response to events. 
-  Storage (File, Block, and Object storage)

> Amazon S3 (object storage)
- Has different storage classes standard, standard infrequent, one zone infrequent, glacier, glacier deep archive, and intelligent tiering.
- S3 Glacier: Data archival and long-term backup. Retrieval types - Standard, Bulk, and Expedited.

> AWS Storage Gateway
- Gives access to virtual unlimited cloud storage but on-premises.

> Amazon VPC
- It lets you create a virtual network for your AWS services to exist in the local IP address range in your local network.

## Day 3:

> CloudFormation
- Used for creating or infrastructure. CloudFormation allows a DevOps engineer to automate the creation of his infrastructure.

> Machine Learning
- AWS services are Amazon Kendra, Amazon Personalize, Amazon Lookout for metrics, Amazon Forcast, Amazon Fraud Detector, Amazon Rekognition, Amazon Polly, Amazon Transcribe, and Amazon Lex.
- Amazon DeepRacer: [Link](https://aws.amazon.com/deepracer/league/)

> Case Studies
![alt text](image.png)
![alt text](image-1.png)
![alt text](image-2.png)
![alt text](image-3.png)
![alt text](image-4.png)
Few more architecture: [Link](https://aws.amazon.com/blogs/architecture/)

## Day 4:

> Cloud Computing
- CapEx vs OpEx: CapEx(Capital Expenditures) are upfront purchases towards fixed assets, and OpEx(Operating expenditures) are funds used to run day-by-day operations.
- Cloud Computing models: Infrastructure as a Service (building blocks), Software as a Service, and Platform as a Service.
- Cloud Deployment models: Private cloud, public cloud, and Hybrid cloud (clouds connected via VPN or direct connect).
- AWS Availability Zones: One or more discrete data centers with redundant power, networking, and connectivity in an AWS region.
- **A region is global and comprises two or more AZs. An AZ is made up of multiple data centers. Multi-AZ deployments provide high availability and fault tolerance.**

> Cloud Adoption Framework
- It has 4 domains: Technology, Process, Organization, and Product.
- It has 4 phases: Envision, Align, Launch, and Scale.
- Well-Architecured Framework Pillars: Security, Cost Optimization, Performance efficiency, Operational Excellence, Reliability, and Sustainability.
- ![alt text](image-5.png)

> AWS Account
- Let's create an AWS account

## Day 5:

> Elastic Cloud Compute (EC2)
- EC2 pricing options: On-Demand, Spot, Reserved instances, Dedicated Hosts, and Savings Plans.
- It offers load balancing. Types of load balancers are Classic, Application (used at layer 7 for flexible application management using HTTP and HTTPS protocols), Gateway, and Network (used at layer 4 using TCP, UDP, and TLS for extreme performance and static IPs).
- Auto Scaling has two types horizontal (increases the number of instances) and vertical (increases the power of the instance)
- Connection: various ways to connect to a Linux EC2 instance: Instance connect, SSH, and System Manager. Whereas RDP is for Windows.

> Containers
- Just think of every container as a separate application. Benefits are Portability, Optional Consistency, Efficiency, Application development, and Less overhead.
- We can use containers when (microservices architecture), (we want the application to be isolated, deployed, and scaled), (support for CI/CD deployments much smoother), and (if we have several repetitive jobs).
- Services provided are
1. Elastic Container registry: it stores all the records of the container.
2. Elastic Container Service: it is fully managed and serverless and supports Docker and Docker Compose CLI.
3. Elastic Kubernetes Service: it is a fully managed open-source system and this supports Kubernetes.
- Fargate is considered serverless and is used to manage containers.

> Lambda Practice Lab
- **Go to the lambda console. Click on the Create function and fill in the details. Write a sample code to print out the name, then deploy the function, configure a test event, and click on test.**
- **We can see the results and then click on the monitor tab and click on view cloud watch logs. Here click on the latest task and there we can see the output of our program.**

> Other Compute services
- Outposts: Fully managed on-premises solutions, supports hybrid deployment models.
- Lightsail: not on-premises, allows quick launch of all resources needed for small projects, has simple UI, has bundles, and is low cost.
- Batch: allows processing large workload into smaller chunks or batches.
- Wavelength: allows users to reach application servers without leaving the 5G mobile network.

## Day 6:

> EC2 Storage options
- EBS is block-level storage used with EC2 instances, EFS is a file system scalable across multiple EC2 instances, and the instance store provides temporary block-level storage directly attached to the instance. 
- Only EBS and EFS offer durable storage solutions. In the instance store the data will be lost if the instance is interrupted. All provide high performance, EBS is particularly known for its provisioned IOPS, EFS is scalable file storage, and instance store for a high I/O operation suitable for temporary data. While EBS and EFS have costs associated with the amount of storage provisioned, the instance store comes at no additional cost, as it's included in the instance price.

> Amazon Simple Storage Service (S3)
- S3 is object storage and is globally acceptable. The bucket is our primary container; within it, we have objects or data files stored in S3 have data, a key (unique within a bucket), and metadata.** Benefits are durability, Scalability, Security, and Versatility. Use cases are Data backup, Web hosting, and Content distribution.

> S3 Storage classes
- Standard: Suitable for frequently accessed data and has high throughput and low latency.
- Intelligent-Tiering: Suitable for data of unpredictable access patterns and designed for savings.
- Standard-Infreqent access: Suitable for less frequently accessed data and requires rapid access when needed.
- One Zone-Infrequent access: Suitable for secondary backup or easily reproducible data. (stores only in one AZ)
- Glacier Instant Retrieval: Designed for immediate access to our archive data.
- Glacier Flexible Retrieval: Designed for data that is accessed only 1-2 times a year and is not immediate.
- Glacier Deep archive: Long time archive and is slow.

> S3 Practice lab
- **First search for S3 and click on the create bucket. The name of the bucket has to be globally unique and click on the enable option in the bucket versioning which allows us to download the previous version of our bucket, we can also enable encryption and finally click on create a bucket.**
- **Now click on the name, click on upload files, and select or sample file. To understand how versioning works edit or sample a file with dummy data and upload the same file to the bucket again.**
- **If we check the data in the uploaded file it has been changed. To resolve this click on our file go to the versions tab select the previous version of or file download it and again upload the downloaded file into the bucket.**

> FSx & Elastic Disaster Recovery
- FSx is tailored for Windows-based workloads. EDR is for swift recovery and minimizing disruptions. FSx offers seamless integration and EDR is important for quick recovery times and cost-effectiveness.

> Elastic Block Store (EBS)
- EBS's key features are persistent storage, highly available and durable, scalable, encrypted, and snapshot.
- EBS Volme types
- 1. Solid State Drive (SSD): faster, more expensive, and ideal for high IOPS.
- 2. Hard Disk Drive (HDD): slower, less expensive, and ideal for throughput tasks.

> AWS Storage Gateway (a hybrid storage service)
The main uses are cost-effective, secure, and seamless integration.
- S3 File Gateway: keeps your data in cloud-native formats.
- Volume Gateway: Provides block storage and offers stored and cache volumes.
- Tape Gateway: For long-term data (the archived data).
- FSx File Gateway: Extends on-premises file system.

## Day 7

- Edge location is a data center that is nearest to the user requesting your content.

> AWS Global Accelerator
- It is a networking service that sends your user traffic to the AWS's global network infrastructure enhancing your application performance and availability.
- Benefits are improved performance, simplified traffic management, security/Reliability, and consistent global user experience.

> Networking
- The Virtual Private Cloud (VPC) has two types of subnets: Public and Private. Also, VPC has an internet gateway and a Route table. Each subnet must be associated with a route table. Security in VPC: Security group(operates at instance level) and Network Access Control List (operates at subnet level, and these are stateless).

> DNS (Amazon Route 53 for AWS)
- Its features are sophisticated traffic routing (types: geolocation, latency-based, weighted round-robin routing).
- Health checks, DNS failover, and scalability & integration.

> AWS Direct Connect
- It is like a private road built exclusively for your use. A few benefits are high-speed data transfer, reduced bandwidth costs, and reliable connection.
- AWS VPN: Site-to-Site VPN (creates a secure connection between your data center or branch office and your AWS environment) and Client VPN (allows secure access to AWS resources or your private network from any location).
- Use direct connect (larger scale data transfer, consistent performance, and sensitive data) and use VPN (encrypted over public network, cost-effective, and quick & easy setup).

## Day 8

> Databases
- relational Database: organized in rows and columns, Amazon Relational Database Service.
- NoSQL Databases: organized as key-value pairs, Amazon DynamoDB.
- In-Memory Databases: stores them in the computer's main memory, Amazon ElastiCache & Amazon MemoryDB for Redis
- Graph Database: Amazon Neptune, used for fraud detection, recommendation systems, and drug discovery.

> AWS Database Migration Service
- It is simple to use, minimal downtime, reliable, and database consolidation.
- AWS Schema Conversion tool: It helps convert our source database's database schema to a format compatible with AWS target databases.

> Amazon DynamoDB
- Features: Performance at scale, fully managed, built-in security, and Backup & restore. (low latency and high performance)
- Use cases: Web and Mobile Applications, Gaming Applications, IoT applications, and E-Commerce Platforms.

> Memory-Based Databases
- They store data in RAM instead of traditional storage.
- Amazon MemoryDB for Redis: Ultra-fast performance, Data Durability. Uses Cases: Cacheing for web applications, Real-Time Analytics, Session Store for Applications, Leaderboard and Gaming, And Geospatial Data processing.

> Continuous Integration / Continuous Deployment (CI/CD)
- It aims to streamline and accelerate the software development lifecycle. Benefits: Automation (Fast, repeatable, and scalable), Manua Effort Avoided (Slow, error-prone, and inconsistent), and Small changes applied frequently (catch bugs while they are small and simple to fix).

> AWS Development tools
- AWS CodeCommit: It is like a private git repository in the cloud.
- AWS CodeBuild: It is a fully managed code service that runs a set of commands we decide. **It can refer to the code stored in the CodeCommit and use them to build deployable artifacts like packages, docker images, etc.**
- AWS CodeDeploy: It is an automated deployment service that allows us to automatically deploy software into EC2 instances, on-premises systems, and lambda.
- AWS CodePipeline: Manages and automates the process (CodeCommit -> CodeBuild -> CodeDeploy -> EC2).

- Creating a S3 bucket and uploading a file using AWS CLI
1. Open the AWS CLI, type **aws s3 mb s3://mybucket-8745468989238** and hit enter.
2. To list the buckets type **aws s3 ls**.
3. Now create a sample file by typing **echo "my new file" >> file.txt**.
4. Now to upload type **aws s3 cp file.txt s3://mybucket-8745468989238**.
5. Type **aws s3 ls s3://mybucket-8745468989238** which shows files in our bucket.

> AWS CodeArtifact
- It is an artifact repository that lets developers securely store, publish, and share software packages (Maven, NPM, and Python). It makes it easy for developers to find the software versions they need. 
- Artifacts like documentation, compiled applications, deployable packages, and libraries.

> Tight Coupling
- Coupling describes the dependencies between the components. This tight coupling is a feature in **monolithic application** where all the components in the application are interdependent. One failed component can bring the entire system down.

> Loose Coupling
- It is a feature in **microservices-based architecture** where all the components operate independently. It doesn't need to wait for other components to be completed.

> Application Integration Services

| Integration Approach    | AWS Service                       |
| :---                    |                              ---: |
| Queues                  | SQS - Simple Queue Service        |
| Notification            | SNS - Simple Notification Service |
| Events                  | EventBridge                       |

> SNS - Simple Notification Service and practice lab
- It allows us to set up, operate, and send notifications. It uses a pub and sub-model which means publish and subscribe. 
- Lab:
1. First we are going to create an SNS topic, so go to the console, search for SNS, and type the topic name in our case we are going to monitor the EC2 so let's name it EC2State and click on create topic.
2. Now we have to subscribe to the topic, so click on Create Subscription, select the topic that we have created, select a protocol which in our case Email, type the email, and click on Create Subscription. You will get a confirmation email, click it and the subscription has been created.
3. Now to test our topic, let's go to the EC2 instance select it, and copy the instance ID, then go to the cloud watch, click on the Create Alarm, click on Select metric, paste our instance ID, click on EC2 pre-instance metrics, again type for StatusCheck, then click on the StatusCheckkFailed_Instance option and hit select metric.
4. We will select the period for 1 minute, change it into Greater/Equal to 1, select "Treat missing data as bad", then hit next. Here we will select our SNS topic which is EC2State, add the notification for all three alarm state triggers, and then hit next.
5. Create a name for the alarm and click Create alarm. Then after some time, we get an email saying "Amazon CloudWatch Alarm "EC2State" in the US East (N. Virginia) region has entered the ALARM state, because "Threshold Crossed:....".
