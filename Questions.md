TEST CLOUD COMPUTING
<h1 align="center">TEST CLOUD COMPUTING</h1>

- 1-You ONLY want to manage Applications and Data. Which type of Cloud Computing model should you use?

    Plataform as a Service (PaaS)

- 2-What is the pricing model of Cloud Computing?

    Pay-as-you-go pricing

- 3-Which Global Infrastructure identity is composed of one or more discrete data centers with redundant power, networking, and connectivity, and are used to deploy infrastructure?

    Avaliability Zones

- 4-Which of the following is NOT one of the Five Characteristics of Cloud Computing?

    Dedicated Support Agent to Help you deploy application

- 5-Which are the 3 pricing fundamentals of the AWS Cloud?

    Compute, Storage, and data transfer out of the AWS Cloud are the 3 pricing fundamentals of the AWS Cloud.

- 6-Which of the following options is NOT a point of consideration when choosing an AWS Region?

    Capacity is unlimited in the cloud, you do not need to worry about it. The 4 points of considerations when choosing an AWS Region are: compliance with data governance and legal requirements, proximity to customers, available services and features within a Region, and pricing.

- 7-Which of the following is NOT an advantage of Cloud Computing?

    Train your employees less. You must train your employees more so they can use the cloud effectively.

- 8-AWS Regions are composed of?

    Two or more avaliability Zones. AWS Regions consist of multiple, isolated, and physically separate Availability Zones within a geographic area.

- 9-Which of the following services has a global scope?

    IAM is a global service (encompasses all regions).

- 10-Which of the following is the definition of Cloud Computing?

    On-demand avaliability of computer systems resources, especially data storage(cloud storage) and computing power, withou direct active management by the user.

- 11-What defines the distribution of responsibilities for security in the AWS Cloud?

    The Shared Responsibility Model defines who is responsible for what in the AWS Cloud.

- 12 - A company would like to benefit from the advantages of the Public Cloud but would like to keep sensitive assets in its own infrastructure. Which deployment model should the company use?

    Using a Hybrid Cloud deployment model allows you to benefit from the flexibility, scalability and on-demand storage access while keeping security and performance of your own infrastructure.

- 13 - What is NOT authorized to do on AWS according to the AWS Acceptable Use Policy?
    
    Run analytics on stolen content

---
<h1 align="center">TEST IAM – Identity and Acess Management</h1>

- 1 - What is a proper definition of IAM Roles?

    An IAM entity that defines a set od permissions for making AWS services request, that will be used by AWS services

- 2 - Which of the following is an IAM Security Tool?
    
    IAM Credentials report lists all your account's users and the status of their various credentials. The other IAM Security Tool is IAM Access Advisor. It shows the service permissions granted to a user and when those services were last accessed.

- 3 - Which answer is INCORRECT regarding IAM Users?

    IAM Users access AWS with the root account credentials. IAM Users access AWS using a username and a password.

- 4 - Which of the following is an IAM best practice?

    Don't use the root user account. You only want to use the root account to create your first IAM user, and for a few account and service management tasks. For every day and administration tasks, use an IAM user with permissions.

- 5 - What are IAM Policies?

    JSON documents to define Users, Groups or Roul's permission

- 6 - Under the shared responsibility model, what is the customer responsible for in IAM?

    Assinging users proper IAM Policies

- 7 - Which of the following statements is TRUE?

    The AWS CLI can interact with AWS using commands in your command-line shell, while the AWS SDK can interact whit AWS programmatically

- 8 - Which principle should you apply regarding IAM Permissions?

    Grant least privilege. That's right! Don't give more permissions than the user needs. 

- 9 - What should you do to increase your root account security?

    You want to enable MFA in order to add a layer of security, so even if your password is stolen, lost or hacked your account is not compromised.

---
<h1 align="center">TEST EC2 - ELASTIC COMPUTE CLOUD</h1>

- 1 - Which EC2 Purchasing Option can provide the biggest discount, but is not suitable for critical jobs or databases?
    Spot Instances are good for short workloads, but are less reliable.

- 2 - Which network security tool can you use to control traffic in and out of EC2 Instances?
    Security Groups operate at instance level and can control traffic.

- 3 - Under the Shared Responsibility Model, who is responsible for operating-system patches and updates on EC2 Instances?
    The customer is responsible for operating-system patches and updates on EC2 Instances, as well as data security on the instances, Security Groups rules, etc.

- 4 - How long can you reserve an EC2 Reserved Instance?
1 year or 3 years terms are available for EC2 Reserved Instances.

- 5 - A company would like to deploy a high-performance computing (HPC) application on EC2. Which EC2 instance type should it choose?
    Compute Optimized EC2 instances are great for compute-intensive workloads requiring high performance processors, such as batch processing, media transcoding, high performance web servers, high performance computing, scientific modeling & machine learning, and dedicated gaming servers.

- 6 - Which of the following is NOT an EC2 Instance Purchasing Option?
    Connect Instance. This EC2 Instance purchasing option does not exist.

- 7 - Which EC2 Purchasing Option should you use for an application you plan on running on a server continuously for 1 year?
    Reserved Instances are good for long workloads. You can reserve instances for 1 or 3 years.

----
<h1 align="center">TEST EC2 INSTANCE STORAGE </h1>

- 1 - Which EC2 Storage would you use to create a shared network file system for your EC2 Instances?
Amazon EFS is a fully managed service that makes it easy to set up, scale, and cost-optimize file storage in the Amazon Cloud.

- 2 - Which service can be used to automate image management processes?
EC2 Image Builder is an automated pipeline for the creation, maintenance, validation, sharing, and deployment of Linux or Windows images for use on AWS and on-premises.

- 3 - Which of the following is a fully managed native Microsoft Windows file system?
Amazon FSx makes it easy and cost effective to launch and run popular file systems that are fully managed by AWS. It comes in two offerings: FSx for Windows File Server (used for business applications), and FSx for Lustre (used for high-performance computing).

- 4 - What are AMIs NOT used for?
You cannot use AMIs to add your IP addresses. IP addresses are added to an instance as you create it.

- 5 - EBS Volumes CANNOT be attached to multiple EC2 instances at a time.
EBS Volumes can be attached to only one EC2 Instance at a time, but EC2 Instances can have multiple EBS Volumes attached to them.

- 6 - An EBS Volume is a network drive you can attach to your instances while they run, so your instances' data persist even after their termination.
True. EBS Volumes allows instances' data to persist even after their termination.

- 7 - Which statement is CORRECT regarding EC2 Instance Store?
EC2 Instance Store has a better I/O performance, but data is lost if: the EC2 instance is stopped or terminated, or when the underlying disk drive fails.

- 8 - What is an EBS Snapshot?
EBS Snapshots are used to backup data on your EBS Volumes at a point in time.

- 9 - Where can you find a third party's AMI so you can use it to launch your EC2 Instance?
You can use AWS Marketplace AMIs to use someone else's AMI.

- 10 - What is an EBS Volume tied to?
EBS Volumes are tied to only one availability zone.

---
<h1 align="center">TESTE ELB & ASG - ELASTIC LOAD BALANCING E AUTO SCALING</h1>

- 1 - What is the main purpose of High Availability in the Cloud?
Applications thriving even in case of a disaster. High Availability means applications running at least in two AZs to survive a data center loss.

- 2 - Which AWS offered Load Balancer should you use to handle hundreds of thousands of connections with low latency?
A Network Load Balancer can handle millions of requests per second with low-latency. It operates at Layer 4, and is best-suited for load-balancing TCP, UDP, and TLS traffic with ultra high-performance.

- 3 - Changing an EC2 Instance Type from a t3a.medium to a t3a.2xlarge is an example of?
Vertical scaling means increasing the size of the instance. Changing from a t3a.medium to a t3a.2xlarge is an example of size increase.

- 4 - What can you use to handle quickly and automatically the changing load on your websites and applications by adding compute resources?
An Auto Scaling Group (ASG) can automatically and quickly scale-in and scale-out to match the changing load on your applications and websites.

- 5 - Which of the following statements is INCORRECT regarding Auto Scaling Groups?
Automatically changing the EC2 Instance Types. Auto Scaling Groups can add or remove instances, but from the same type. They cannot change the EC2 Instances Types on the fly.

- 6 - Which Load Balancer is best suited for HTTP/HTTPS load balancing traffic?
Application Load Balancers are used for HTTP and HTTPS load balancing. They are the best-suited for this kind of traffic.

- 7 - Which of the following is NOT an Auto Scaling Strategy?
Active Scaling. This is not a scaling strategy. Auto Scaling Strategies include: Manual Scaling, Dynamic Scaling (Simple/Step Scaling, Target Tracking Scaling, Scheduled Scaling), and Predictive Scaling.

- 8 - Which AWS service offers easy horizontal scaling of compute capacity?
Auto Scaling Groups (ASG) offers the capacity to scale-out and scale-in by adding or removing instances based on demand.

- 9 - Which of the following statements is NOT a feature of Load Balancers?
Back-end Autoscaling. Load Balancers cannot help with back-end autoscaling. You should use Auto Scaling Groups.

---
<h1 align="center">TEST S3</h1>

- 1 - Which S3 Storage Class is the most cost-effective for archiving data with no retrieval time requirement?
Amazon Glacier Deep Archive is the most cost-effective option if you want to archive data and do not have a retrieval time requirement. You can retrieve data in 12 or 48 hours.

- 2 - Which S3 feature should you use if you want to make sure that a policy will no longer be changed?
S3 Glacier Vault Lock allows you to easily deploy and enforce compliance controls for individual S3 Glacier vaults with a vault lock policy. You can specify controls such as “write once read many” (WORM) in a vault lock policy and lock the policy from future edits. Once locked, the policy can no longer be changed.

- 3 - What hybrid AWS service is used to allow on-premises servers to seamlessly use the AWS Cloud at the storage layer?
AWS Storage Gateway is a hybrid cloud storage service that gives you on-premises access to virtually unlimited cloud storage.

- 4 - Which of the following services is a petabyte-scale data moving service (as a fleet) in or out of AWS with computing capabilities?
Snowball Edge is best-suited to move petabytes of data and offers computing capabilities. Be careful, it's recommended to use a fleet of Snowballs to move less than 10PBs of data. Over this quantity, it's better-suited to use Snowmobile.

- 5 - Which of the following is an exabytes-scale data moving service in or out of AWS?
Snowmobile is used to move exabytes of data in or out of AWS (1 EB=1,000 PBs=1,000,000 TBs).

- 6 - What are Objects NOT composed of?
Access Keys are used to sign programmatic requests to the AWS CLI or AWS API.

- 7 - Where are objects stored in Amazon S3?
Buckets store objects in Amazon S3.

- 8 - A research team deployed in a location with low-internet connection would like to move 5 TBs of data to the Cloud. Which service can it use?
AWS Snowcone is a small, portable, rugged, and secure edge computing and data transfer device. It provides up to 8 TB of usable storage.

- 9 - What can you use to define actions to move S3 objects between different storage classes?
Lifecycle Rules can be used to define when S3 objects should be transitioned to another storage class or when objects should be deleted after some time.

- 10 - A non-profit organization needs to regularly transfer petabytes of data to the cloud and to have access to local computing capacity. Which service can help with this task?
Snowball Edge Storage Optimized devices are well suited for large-scale data migrations and recurring transfer workflows, as well as local computing with higher capacity needs.

- 11 - Which S3 Storage Class is suitable for less frequently accessed data, but with rapid access when needed, while keeping a high durability and allowing an Availability Zone failure?
Amazon S3 Standard-Infrequent Access allow you to store infrequently accessed data, with rapid access when needed, has a high durability, and is stored in several Availability Zones to avoid data loss in case of a disaster. It can be used to store data for disaster recovery, backups, etc.


---
<h1 align="center">TEST DATABASE</h1>

- 1 - You want to create a decentralized blockchain on AWS. Which AWS service would you use?
Amazon Managed Blockchain is a fully managed service that makes it easy to create and manage scalable blockchain networks using the popular open source frameworks Hyperledger Fabric and Ethereum. It allows multiple parties to execute transactions without the need of a trusted, central authority.

- 2 - Which AWS database is a data warehouse?
Amazon Redshift is a fully managed, petabyte-scale data warehouse service in the cloud.

- 3 - Which AWS service is always serverless and has SQL capabilities?
Amazon Athena is an interactive query service that makes it easy to analyze data in Amazon S3 using standard SQL. Athena is serverless, so there is no infrastructure to manage, and you pay only for the queries that you run.

- 4 - You would like to use a serverless service to prepare data so it can be loaded for analytics. Which service would you use?
AWS Glue is a fully managed extract, transform, and load (ETL) service that makes it easy for customers to prepare and load their data for analytics.

- 5 - Which relational database is a proprietary technology from AWS and is cloud-optimized?
Amazon Aurora is a MySQL and PostgreSQL-compatible relational database built for the cloud, that combines the performance and availability of traditional enterprise databases with the simplicity and cost-effectiveness of open source databases. It is a proprietary technology from AWS.

- 6 - You would like to migrate databases to AWS while still being able to use the database during the migration. What service allows you to do this?
AWS Database Migration Service helps you migrate databases to AWS quickly and securely. The source database remains fully operational during the migration, minimizing downtime to applications that rely on the database.

- 7 - How can you create Hadoop clusters to analyze and process a vast amount of data?
Amazon EMR is a web service that enables businesses, researchers, data analysts, and developers to easily and cost-effectively process vast amounts of data. EMR helps creating Hadoop clusters (Big Data) to analyze and process vast amount of data

- 8 - Which in-memory AWS database can you use to reduce the load off databases and has high performance, low latency?
Amazon ElastiCache is a web service that makes it easy to deploy and run Memcached or Redis protocol-compliant server nodes in the cloud. ElastiCache caches are in-memory databases with high performance, low latency. They help reduce load off databases for read intensive workloads.

- 9 - What is the name of a central repository to store structural and operational metadata for data assets in AWS Glue?
The AWS Glue Data Catalog is a central repository to store structural and operational metadata for all your data assets. For a given data set, you can store its table definition, physical location, add business relevant attributes, as well as track how this data has changed over time.

- 10 - Which of the following databases is a managed service with SQL capability suited for Online Transaction Processing (OLTP)?
Amazon Relational Database Service (Amazon RDS) is a SQL managed service that makes it easy to set up, operate, and scale a relational database in the cloud. It is suited for OLTP workloads

- 11 - Which AWS service is an immutable ledger database?
Amazon QLDB is a fully managed ledger database that provides a transparent, immutable, and cryptographically verifiable transaction log owned by a central trusted authority. Amazon QLDB tracks each and every application data change and maintains a complete and verifiable history of changes over time.

- 12 - You would like to set up a NoSQL database that can scale with no downtime and can handle millions of requests per second. Which AWS database is best suited for this work?
DynamoDB is a fast and flexible non-relational database service for any scale. It can scale with no downtime, it can process millions of requests per second, and is fast and consistent in performance.

- 13 - Which AWS service can create complex graphs for fraud detection?
Amazon Neptune is a fast, reliable, fully-managed graph database service that makes it easy to build and run applications that work with highly connected datasets. It can be used for knowledge graphs, fraud detection, recommendations engines, social networking, etc.

- 14 - Which AWS serverless service can use machine learning-powered business intelligence to create interactive dashboards such as business analytics?
Amazon QuickSight is a fast, cloud-powered business intelligence (BI) service that makes it easy for you to deliver insights to everyone in your organization. You can create and publish interactive dashboards.

- 15 - A company would like to set up a fully managed MongoDB database. Which AWS database is best-suited for this task?
Amazon DocumentDB (with MongoDB compatibility) is a fast, calable, highly available, and fully managed document database service that supports MongoDB workloads.

- 16 - Which exclusive DynamoDB feature is an in-memory cache that can improve your performance up to 10x?
Amazon DynamoDB Accelerator (DAX) is a fully managed, highly available, in-memory cache for Amazon DynamoDB that delivers up to a 10 times performance improvement—from milliseconds to microseconds—even at millions of requests per second.

- 17 - O objetivo principal das implantações do RDS Multi-AZ é a alta disponibilidade, enquanto o objetivo principal das réplicas de leitura do RDS é a escalabilidade.
True. RDS Multi-AZ deployments’ main purpose is high availability, and RDS Read replicas’ main purpose is scalability. Moreover, Multi-Region deployments’ main purpose is disaster recovery and local performance.

---
<h1 align="center">TESTE OTHER COMPUTE SERVICES QUIS</h1>

- 1 - How do you get charged in AWS Lambda?
In AWS Lambda, you are charged per request and compute time, that's it.

- 2 - You would like a serverless service to launch Docker containers with no infrastructure to provision. Which AWS service should you use?
Fargate allows you to launch Docker containers on AWS, and you don't need to provision and maintain the infrastructure (=no EC2 instances to manage). It is serverless.

- 3 - A complete cloud beginner would like to create a simple application with predictable pricing. What service should this person use?
Amazon Lightsail is designed to be the easiest way to launch and manage a virtual private server with AWS. Lightsail plans include everything you need to jumpstart your project – a virtual machine, SSD- based storage, data transfer, DNS management, and a static IP address – for a low, predictable price. It can be used to create a simple web application, a website or a dev/test environment.

- 4 - What is the name of the software development platform that allows you to run applications the same way, regardless of where they are run?
Docker is a software development platform that allows you to run applications the same way, regardless of where they are run. It can scale containers up and down within seconds.

- 5 - How would you best describe "event-driven" in AWS Lambda?
"Event-driven" in Lambda means that functions are invoked when needed. They are triggered.

- 6 - Which AWS service allows you to launch Docker containers on AWS, but requires you to provision and maintain the infrastructure?
ECS allows you to launch Docker containers on AWS, but you must provision and maintain the infrastructure (i.e. EC2 instances).

- 7 - Which of the following statements is INCORRECT regarding the definition of the term "serverless"?
Serverless does not mean that there are no servers, you just do not manage, provision and see them, but they do exist.

- 8 - Which of the following statements is NOT a feature of AWS Lambda?
Definition of a minimum and maximm of EC2 instances running. This is a feature of Auto Scaling Groups, not AWS Lambda.
 
- 9 - A company needs to run thousands of jobs but would like to NOT manage the compute resources. What service can it use?
AWS Batch enables developers, scientists, and engineers to easily and efficiently run hundreds of thousands of batch computing jobs on AWS. AWS Batch dynamically provisions the optimal quantity and type of compute resources (e.g., CPU or memory-optimized instances) based on the volume and specific resource requirements of the batch jobs submitted.

- 10 - Where should you store your private Docker images so they can be run by ECS or Fargate?
Elastic Container Registry (ECR) is a service where you store your Docker image so they can be run by ECS or Fargate.

- 11 - Which AWS serverless service can be used by developers to create APIs?
Amazon API Gateway is a fully managed serverless service that makes it easy for developers to create, publish, maintain, monitor, and secure APIs at any scale.
