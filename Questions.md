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


TEST EC2 INSTANCE STORAGE 
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
