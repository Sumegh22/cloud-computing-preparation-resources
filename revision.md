# AWS Cognito
* Cognito User Pools Authorises api calls within api gateway.
*  Cognito identity pools provide aws credentials to users to access aws resources.
  
# S3
* To setup a one time copy of S3 bucket data from one region to another region You can use Aws snowball, Use S3 Sync command, or Setup S3 batch replication to copy objects across S3 buckets in another Region using S3 console and delete replication configuration.

* Bucket policies in Amazon S3 can be used to add or deny permissions across some or all of the objects within a single bucket. Policies can be attached to users, groups, or Amazon S3 buckets, enabling centralized management of permissions. With bucket policies, you can grant users within your AWS Account or other AWS Accounts access to your Amazon S3 resources.

* You can further restrict access to specific resources based on certain conditions. For example, you can restrict access based on request time (Date Condition), whether the request was sent using SSL (Boolean Conditions), a requester’s IP address (IP Address Condition), or based on the requester's client application (String Conditions). To identify these conditions, you use policy keys.

Types of access control in Amazon S3
<img width="1372" height="960" alt="image" src="https://github.com/user-attachments/assets/c7e48854-ab46-4bae-8267-cfa528ba2e06" />

* When A process replaces an existing object and immediately tries to read it. Amazon S3 always returns the latest version of the object
* Amazon S3 delivers strong read-after-write consistency automatically, without changes to performance or availability, without sacrificing regional isolation for applications, and at no additional cost.
* After a successful write of a new object or an overwrite of an existing object, any subsequent read request immediately receives the latest version of the object. Amazon S3 also provides strong consistency for list operations, so after a write, you can immediately perform a listing of the objects in a bucket with any changes reflected.
* Strong read-after-write consistency helps when you need to immediately read an object after a write. For example, strong read-after-write consistency when you often read and list immediately after writing objects.
* To summarize, all Amazon S3 GET, PUT, and LIST operations, as well as operations that change object tags, ACLs, or metadata, are strongly consistent. What you write is what you will read, and the results of a LIST will be an accurate reflection of what’s in the bucket.
### The minimum storage duration is 30 days before you can transition objects from Amazon S3 Standard to Amazon S3 One Zone-IA or Amazon S3 Standard-IA


# Aws Kinesis 
* Use aws kinesis data streams to process stream data in near real time.
**Enhanced Fanout feature of Amazon Kinesis Data Streams:**
* Amazon Kinesis Data Streams (KDS) is a massively scalable and durable real-time data streaming service. KDS can continuously capture gigabytes of data per second from hundreds of thousands of sources such as website clickstreams, database event streams, financial transactions, social media feeds, IT logs, and location-tracking events.

* By default, the 2MB/second/shard output is shared between all of the applications consuming data from the stream. You should use enhanced fan-out if you have multiple consumers retrieving data from a stream in parallel. With enhanced fan-out developers can register stream consumers to use enhanced fan-out and receive their own 2MB/second pipe of read throughput per shard, and this throughput automatically scales with the number of shards in a stream.

Amazon Kinesis Data Streams Fanout:
<img width="1586" height="1106" alt="image" src="https://github.com/user-attachments/assets/dc520287-3ed4-4016-8e2a-b83bde109f5c" />


<img width="1506" height="1270" alt="image" src="https://github.com/user-attachments/assets/c1253a54-a222-4957-8fae-4a3eaf9edc69" />

--------------------


# AWS Rds and Databases 
1. Use read replica to significantly reduce load on db.
2. Amazon RDS - Amazon Relational Database Service (Amazon RDS) makes it easy to set up, operate, and scale a relational database in the cloud. It provides cost-efficient and resizable capacity while automating time-consuming administration tasks such as hardware provisioning, database setup, patching, and backups. Relational databases are not a good fit to store data in key-value pairs.


# AWS NFS to EFS DataSync

* Configure an AWS DataSync agent on the on-premises server that has access to the NFS file system. Transfer data over the AWS Direct Connect connection to an AWS PrivateLink interface VPC endpoint for Amazon EFS by using a private VIF. Set up an AWS DataSync scheduled task to send the video files to the Amazon EFS file system every 24 hours

* AWS DataSync is an online data transfer service that simplifies, automates, and accelerates copying large amounts of data between on-premises storage systems and  AWS Storage services, as well as between AWS Storage services.

* You can use AWS DataSync to migrate data located on-premises, at the edge, or in other clouds to Amazon S3, Amazon EFS, Amazon FSx for Windows File Server, Amazon FSx for Lustre, Amazon FSx for OpenZFS, and Amazon FSx for NetApp ONTAP.

* AWS DataSync:  

via - https://aws.amazon.com/datasync/

* To establish a private connection between your virtual private cloud (VPC) and the Amazon EFS API, you can create an interface VPC endpoint. You can also access the interface VPC endpoint from on-premises environments or other VPCs using AWS VPN, AWS Direct Connect, or VPC peering.

* AWS Direct Connect provides three types of virtual interfaces: public, private, and transit.

* AWS Direct Connect VIFs:  via - https://aws.amazon.com/premiumsupport/knowledge-center/public-private-interface-dx/

* For the given use case, you can send data over the Direct Connect connection to an AWS PrivateLink interface VPC endpoint for Amazon EFS by using a private VIF.

* Using task scheduling in AWS DataSync, you can periodically execute a transfer task from your source storage system to the destination. You can use the DataSync scheduled task to send the video files to the Amazon EFS file system every 24 hours.

# VPC 

VPC sharing (part of Resource Access Manager) allows multiple AWS accounts to create their application resources such as Amazon EC2 instances, Amazon RDS databases, Amazon Redshift clusters, and AWS Lambda functions, into shared and centrally-managed Amazon Virtual Private Clouds (VPCs). To set this up, the account that owns the VPC (owner) shares one or more subnets with other accounts (participants) that belong to the same organization from AWS Organizations. After a subnet is shared, the participants can view, create, modify, and delete their application resources in the subnets shared with them. Participants cannot view, modify, or delete resources that belong to other participants or the VPC owner.

You can share Amazon VPCs to leverage the implicit routing within a VPC for applications that require a high degree of interconnectivity and are within the same trust boundaries. This reduces the number of VPCs that you create and manage while using separate accounts for billing and access control.

-----------


# Rds for Postgres and Mysql (Latency even with Read replicas)

* Use Amazon Aurora Global Database to enable fast local reads with low latency in each region

* Amazon Aurora is a MySQL and PostgreSQL-compatible relational database built for the cloud, that combines the performance and availability of traditional enterprise databases with the simplicity and cost-effectiveness of open source databases.
* Amazon Aurora features a distributed, fault-tolerant, self-healing storage system that auto-scales up to 64TB per database instance. Aurora is not an in-memory database.

* Amazon Aurora Global Database is designed for globally distributed applications, allowing a single Amazon Aurora database to span multiple AWS regions.
*  It replicates your data with no impact on database performance, enables fast local reads with low latency in each region, and provides disaster recovery from region-wide outages. Amazon Aurora Global Database is the correct choice for the given use-case.

* Amazon Aurora Global Database Features:  via - https://aws.amazon.com/rds/aurora/global-database/


# Ec2 application behind and ASG

## Amazon EC2 dedicated instances 
- Dedicated instances are Amazon EC2 instances that run in a VPC on hardware that's dedicated to a single customer. Your dedicated instances are physically isolated at the host hardware level from instances that belong to other AWS accounts. Dedicated instances may share hardware with other instances from the same AWS account that are not dedicated instances. Dedicated instances cannot be used for existing server-bound software licenses.

## Amazon EC2 on-demand instances

## Amazon EC2 reserved instances (RI)
Amazon EC2 presents a virtual computing environment, allowing you to use web service interfaces to launch instances with a variety of operating systems, load them with your custom application environment, manage your network’s access permissions, and run your image using as many or few systems as you desire.

## Amazon EC2 provides the following purchasing options to enable you to optimize your costs based on your needs:

* On-Demand Instances – Pay, by the second, for the instances that you launch.

* Reserved Instances (RI) – Reduce your Amazon EC2 costs by making a commitment to a consistent instance configuration, including instance type and Region, for a term of 1 or 3 years.

* Neither on-demand instances nor reserved instances can be used for existing server-bound software licenses.

### Amazon EC2 dedicated hosts

* You can use Dedicated Hosts to launch Amazon EC2 instances on physical servers that are dedicated for your use. Dedicated Hosts give you additional visibility and control over how instances are placed on a physical server, and you can reliably use the same physical server over time. As a result, Dedicated Hosts enable you to use your existing server-bound software licenses like Windows Server and address corporate compliance and regulatory requirements

<img width="1656" height="1156" alt="image" src="https://github.com/user-attachments/assets/b58b3956-5543-4f77-984f-04ce4ed85de5" />

* To make it more resilient and reduce load on app

* You can only use a launch template to provision capacity across multiple instance types using both On-Demand Instances and Spot Instances to achieve the desired scale, performance, and cost

* A launch template is similar to a launch configuration, in that it specifies instance configuration information such as the ID of the Amazon Machine Image (AMI), the instance type, a key pair, security groups, and the other parameters that you use to launch EC2 instances. Also, defining a launch template instead of a launch configuration allows you to have multiple versions of a template.

* With launch templates, you can provision capacity across multiple instance types using both On-Demand Instances and Spot Instances to achieve the desired scale, performance, and cost. Hence this is the correct option.

* You can use Amazon Aurora replicas and Amazon CloudFront distribution to make the application more resilient to spikes in request rates.

Use Amazon Aurora Replica

* Amazon Aurora Replicas have two main purposes. You can issue queries to them to scale the read operations for your application. You typically do so by connecting to the reader endpoint of the cluster. That way, Aurora can spread the load for read-only connections across as many Aurora Replicas as you have in the cluster. Amazon Aurora Replicas also help to increase availability. If the writer instance in a cluster becomes unavailable, Aurora automatically promotes one of the reader instances to take its place as the new writer. Up to 15 Aurora Replicas can be distributed across the Availability Zones (AZs) that a DB cluster spans within an AWS Region.

* Use Amazon CloudFront distribution in front of the Application Load Balancer

* Amazon CloudFront is a fast content delivery network (CDN) service that securely delivers data, videos, applications, and APIs to customers globally with low latency, high transfer speeds, all within a developer-friendly environment. CloudFront points of presence (POPs) (edge locations) make sure that popular content can be served quickly to your viewers. Amazon CloudFront also has regional edge caches that bring more of your content closer to your viewers, even when the content is not popular enough to stay at a POP, to help improve performance for that content.

* Amazon CloudFront offers an origin failover feature to help support your data resiliency needs. Amazon CloudFront is a global service that delivers your content through a worldwide network of data centers called edge locations or points of presence (POPs). If your content is not already cached in an edge location, Amazon CloudFront retrieves it from an origin that you've identified as the source for the definitive version of the content.


# AWS Shield 
* AWS Shield - AWS Shield is a managed Distributed Denial of Service (DDoS) protection service that safeguards applications running on AWS. AWS Shield provides always-on detection and automatic inline mitigations that minimize application downtime and latency.
* There are two tiers of AWS Shield - Standard and Advanced. AWS Shield cannot be used to improve application resiliency to handle spikes in traffic.

# AWS Global Accelerator - 
* AWS Global Accelerator is a service that improves the availability and performance of your applications with local or global users. It provides static IP addresses that act as a fixed entry point to your application endpoints in a single or multiple AWS Regions, such as your Application Load Balancers, Network Load Balancers or Amazon EC2 instances.
* Amazon Global Accelerator is a good fit for non-HTTP use cases, such as gaming (UDP), IoT (MQTT), or Voice over IP, as well as for HTTP use cases that specifically require static IP addresses or deterministic, fast regional failover.
  
*  AUse AWS Global Accelerator to distribute a portion of traffic to a particular deployment

* AWS Global Accelerator is a network layer service that directs traffic to optimal endpoints over the AWS global network, this improves the availability and performance of your internet applications. It provides two static anycast IP addresses that act as a fixed entry point to your application endpoints in a single or multiple AWS Regions, such as your Application Load Balancers, Network Load Balancers, Elastic IP addresses or Amazon EC2 instances, in a single or in multiple AWS regions.

* AWS Global Accelerator uses endpoint weights to determine the proportion of traffic that is directed to endpoints in an endpoint group, and traffic dials to control the percentage of traffic that is directed to an endpoint group (an AWS region where your application is deployed).

While relying on the DNS service is a great option for blue/green deployments, it may not fit use-cases that require a fast and controlled transition of the traffic. Some client devices and internet resolvers cache DNS answers for long periods; this DNS feature improves the efficiency of the DNS service as it reduces the DNS traffic across the Internet, and serves as a resiliency technique by preventing authoritative name-server overloads. The downside of this in blue/green deployments is that you don’t know how long it will take before all of your users receive updated IP addresses when you update a record, change your routing preference or when there is an application failure.

With AWS Global Accelerator, you can shift traffic gradually or all at once between the blue and the green environment and vice-versa without being subject to DNS caching on client devices and internet resolvers, traffic dials and endpoint weights changes are effective within seconds.

# AWS Direct Connect - 
* AWS Direct Connect lets you establish a dedicated network connection between your network and one of the AWS Direct Connect locations. Using industry-standard 802.1q VLANs, this dedicated connection can be partitioned into multiple virtual interfaces.
*  AWS Direct Connect does not involve the Internet; instead, it uses dedicated, private network connections between your intranet and Amazon VPC.

# Amazon Route 53 
* Route 53 weighted routing to spread traffic across different deployments - Weighted routing lets you associate multiple resources with a single domain name (example.com) or subdomain name (acme.example.com) and choose how much traffic is routed to each resource. This can be useful for a variety of purposes, including load balancing and testing new versions of the software. DNS caching is a negative behavior for a use case where you wantt o reoute specific load to a destination.

# Load Balancing 
* Use Elastic Load Balancing (ELB) to distribute traffic across deployments - Elastic Load Balancing (ELB) can distribute traffic across healthy instances. You can also use the Application Load Balancers weighted target groups feature for blue/green deployments as it does not rely on the DNS service. In addition you don’t need to create new ALBs for the green environment. As the use-case refers to a global application, so this option cannot be used for a multi-Region solution which is needed for the given requirement.

# Aws CodeDelploy 
* Use AWS CodeDeploy deployment options to choose the right deployment - In AWS CodeDeploy, a deployment is the process, and the components involved in the process, of installing content on one or more instances.
* This content can consist of code, web and configuration files, executables, packages, scripts, and so on. AWS CodeDeploy deploys content that is stored in a source repository, according to the configuration rules you specify. Blue/Green deployment is one of the deployment types that CodeDeploy supports. CodeDeploy is not meant to distribute traffic across instances, so this option is incorrect.

# Aws Config
* Leverage AWS Config managed rule to check if any third-party SSL/TLS certificates imported into ACM are marked for expiration within 30 days. Configure the rule to trigger an Amazon SNS notification to the security team if any certificate expires within 30 days

* AWS Certificate Manager is a service that lets you easily provision, manage, and deploy public and private Secure Sockets Layer/Transport Layer Security (SSL/TLS) certificates for use with AWS services and your internal connected resources. SSL/TLS certificates are used to secure network communications and establish the identity of websites over the Internet as well as resources on private networks.

* AWS Config provides a detailed view of the configuration of AWS resources in your AWS account. This includes how the resources are related to one another and how they were configured in the past so that you can see how the configurations and relationships change over time.

 via - https://docs.aws.amazon.com/config/latest/developerguide/how-does-config-work.html

* AWS Config provides AWS-managed rules, which are predefined, customizable rules that AWS Config uses to evaluate whether your AWS resources comply with common best practices.
* You can leverage an AWS Config managed rule to check if any ACM certificates in your account are marked for expiration within the specified number of days. Certificates provided by ACM are automatically renewed. ACM does not automatically renew the certificates that you import. The rule is NON_COMPLIANT if your certificates are about to expire.

 via - https://docs.aws.amazon.com/config/latest/developerguide/how-does-config-work.html

You can configure AWS Config to stream configuration changes and notifications to an Amazon SNS topic. For example, when a resource is updated, you can get a notification sent to your email, so that you can view the changes. You can also be notified when AWS Config evaluates your custom or managed rules against your resources.

# AWS Lambda

* With AWS Lambda, you can run code without provisioning or managing servers. You pay only for the compute time that you consume—there’s no charge when your code isn’t running.
* You can run code for virtually any type of application or backend service—all with zero administration.
AWS Lambda can be combined with DynamoDB to process and capture the key-value data from the IoT sources.


# Amazon DynamoDB
* Amazon DynamoDB is a key-value and document database that delivers single-digit millisecond performance at any scale.
* It's a fully managed, multi-region, multi-master, durable database with built-in security, backup and restore, and in-memory caching for internet-scale applications.
* Amazon DynamoDB is a NoSQL database and it's best suited to store data in key-value pairs.
* Amazon DynamoDB Accelerator (DAX) is a fully managed, highly available, in-memory cache for Amazon DynamoDB that delivers up to a 10 times performance improvement—from       milliseconds to microseconds—even at millions of requests per second.
* Amazon DynamoDB Accelerator (DAX) is tightly integrated with Amazon DynamoDB—you simply provision a DAX cluster, use the DAX client SDK to point your existing Amazon DynamoDB API calls at the DAX cluster, and let DAX handle the rest. Because DAX is API-compatible with Amazon DynamoDB, you don't have to make any functional application code changes. DAX is used to natively cache Amazon DynamoDB reads.


# Amazon Redshift - 
* Amazon Redshift is a fully-managed petabyte-scale cloud-based data warehouse product designed for large scale data set storage and analysis. You cannot use Redshift to capture data in key-value pairs from the IoT sources, so this option is not correct.

# Amazon ElastiCache - 
* Amazon ElastiCache allows you to seamlessly set up, run, and scale popular open-Source compatible in-memory data stores in the cloud. Build data-intensive apps or boost the performance of your existing databases by retrieving data from high throughput and low latency in-memory data stores.
*  Amazon ElastiCache is a popular choice for real-time use cases like Caching, Session Stores, Gaming, Geospatial Services, Real-Time Analytics, and Queuing.
* Elasticache is used as a caching layer in front of relational databases. It is not a good fit to store data in key-value pairs from the IoT sources, so this option is not correct.
* Amazon ElastiCache is an ideal front-end for data stores such as Amazon RDS, providing a high-performance middle tier for applications with extremely high request rates and/or low latency requirements. The best part of caching is that it’s minimally invasive to implement and by doing so, your application performance regarding both scale and speed is dramatically improved.

----------------------

# Que : 
1. A retail company maintains an AWS Direct Connect connection to AWS and has recently migrated its data warehouse to AWS. The data analysts at the company query the data warehouse using a visualization tool. The average size of a query returned by the data warehouse is 60 megabytes and the query responses returned by the data warehouse are not cached in the visualization tool. Each webpage returned by the visualization tool is approximately 600 kilobytes.

Which of the following options offers the LOWEST data transfer egress cost for the company?

### Ans 
```
Deploy the visualization tool in the same AWS region as the data warehouse. Access the visualization tool over a Direct Connect connection at a location in the same region

AWS Direct Connect is a networking service that provides an alternative to using the internet to connect to AWS. Using AWS Direct Connect, data that would have previously been transported over the internet is delivered through a private network connection between your on-premises data center and AWS.

For the given use case, the main pricing parameter while using the AWS Direct Connect connection is the Data Transfer Out (DTO) from AWS to the on-premises data center. DTO refers to the cumulative network traffic that is sent through AWS Direct Connect to destinations outside of AWS. This is charged per gigabyte (GB), and unlike capacity measurements, DTO refers to the amount of data transferred, not the speed.

 via - https://aws.amazon.com/directconnect/pricing/

Each query response is 60 megabytes in size and each webpage for the visualization tool is 600 kilobytes in size. If you deploy the visualization tool in the same AWS region as the data warehouse, then you only need to pay for the 600 kilobytes of DTO charges for the webpage. Therefore this option is correct.

However, if you deploy the visualization tool on-premises, then you need to pay for the 60 MB of DTO charges for the query response from the data warehouse to the visualization tool.

Incorrect options:

Deploy the visualization tool in the same AWS region as the data warehouse. Access the visualization tool over the internet at a location in the same region

Deploy the visualization tool on-premises. Query the data warehouse over the internet at a location in the same AWS region

Data transfer pricing over AWS Direct Connect is lower than data transfer pricing over the internet, so both of these options are incorrect.

Deploy the visualization tool on-premises. Query the data warehouse directly over an AWS Direct Connect connection at a location in the same AWS region - As mentioned in the explanation above, if you deploy the visualization tool on-premises, then you need to pay for the 60 megabytes of DTO charges for the query response from the data warehouse to the visualization tool. So this option is incorrect.
```
### References:
* https://aws.amazon.com/directconnect/pricing/
* https://aws.amazon.com/getting-started/hands-on/connect-data-center-to-aws/services-costs/
* https://aws.amazon.com/directconnect/faqs/


# Amazon GuardDuty 
* Use Amazon GuardDuty to monitor any malicious activity on data stored in Amazon S3. Use Amazon Macie to identify any sensitive data stored on Amazon S3

* Amazon GuardDuty offers threat detection that enables you to continuously monitor and protect your AWS accounts, workloads, and data stored in Amazon S3. GuardDuty analyzes continuous streams of meta-data generated from your account and network activity found in AWS CloudTrail Events, Amazon VPC Flow Logs, and DNS Logs. It also uses integrated threat intelligence such as known malicious IP addresses, anomaly detection, and machine learning to identify threats more accurately.
* References: https://aws.amazon.com/guardduty/

# Macie 
* How Amazon GuardDuty works:  via - https://aws.amazon.com/guardduty/

* Amazon Macie is a fully managed data security and data privacy service that uses machine learning and pattern matching to discover and protect your sensitive data on Amazon S3. Macie automatically detects a large and growing list of sensitive data types, including personally identifiable information (PII) such as names, addresses, and credit card numbers. It also gives you constant visibility of the data security and data privacy of your data stored in Amazon S3.

* How Amazon Macie works:  via - https://aws.amazon.com/macie/
* https://aws.amazon.com/macie/

# NAT Gateway 
* NAT instance can be used as a bastion server
* Security Groups can be associated with a NAT instance
* NAT instance supports port forwarding

A NAT instance or a NAT Gateway can be used in a public subnet in your VPC to enable instances in the private subnet to initiate outbound IPv4 traffic to the Internet.

How NAT Gateway works:  via - https://docs.aws.amazon.com/vpc/latest/userguide/vpc-nat-gateway.html

How NAT Instance works:  via - https://docs.aws.amazon.com/vpc/latest/userguide/VPC_NAT_Instance.html

Please see this high-level summary of the differences between NAT instances and NAT gateways relevant to the options described in the question:

via - https://docs.aws.amazon.com/vpc/latest/userguide/vpc-nat-comparison.html

* Reference: https://docs.aws.amazon.com/vpc/latest/userguide/vpc-nat-comparison.html

# Amazon FSx for Lustre

* Amazon FSx for Lustre makes it easy and cost-effective to launch and run the world’s most popular high-performance file system. It is used for workloads such as machine learning, high-performance computing (HPC), video processing, and financial modeling. The open-source Lustre file system is designed for applications that require fast storage – where you want your storage to keep up with your compute. FSx for Lustre integrates with Amazon S3, making it easy to process data sets with the Lustre file system. When linked to an S3 bucket, an FSx for Lustre file system transparently presents S3 objects as files and allows you to write changed data back to S3.

* FSx for Lustre provides the ability to both process the 'hot data' in a parallel and distributed fashion as well as easily store the 'cold data' on Amazon S3. Therefore this option is the BEST fit for the given problem statement.


# Amazon FSx for Windows File Server
- Amazon FSx for Windows File Server provides fully managed, highly reliable file storage that is accessible over the industry-standard Service Message Block (SMB) protocol. It is built on Windows Server, delivering a wide range of administrative features such as user quotas, end-user file restore, and Microsoft Active Directory (AD) integration. FSx for Windows does not allow you to present S3 objects as files and does not allow you to write changed data back to S3. Therefore you cannot reference the "cold data" with quick access for reads and updates at low cost. Hence this option is not correct.

# Amazon EMR 
- Amazon EMR is the industry-leading cloud big data platform for processing vast amounts of data using open source tools such as Apache Spark, Apache Hive, Apache HBase, Apache Flink, Apache Hudi, and Presto. Amazon EMR uses Hadoop, an open-source framework, to distribute your data and processing across a resizable cluster of Amazon EC2 instances. EMR does not offer the same storage and processing speed as FSx for Lustre. So it is not the right fit for the given high-performance workflow scenario.

# AWS Glue 
- AWS Glue is a fully managed extract, transform, and load (ETL) service that makes it easy for customers to prepare and load their data for analytics. AWS Glue job is meant to be used for batch ETL data processing. AWS Glue does not offer the same storage and processing speed as FSx for Lustre. So it is not the right fit for the given high-performance workflow scenario.

References:
* https://aws.amazon.com/fsx/lustre/
* https://aws.amazon.com/fsx/windows/faqs/

# Aws shield billing 

If your organization has multiple AWS accounts, then you can subscribe multiple AWS Accounts to AWS Shield Advanced by individually enabling it on each account using the AWS Management Console or API. You will pay the monthly fee once as long as the AWS accounts are all under a single consolidated billing, and you own all the AWS accounts and resources in those accounts.
Consolidated billing has not been enabled. All the AWS accounts should fall under a single consolidated billing for the monthly fee to be charged only once

AWS Shield Advanced does offer protection to resources outside of AWS. This should not cause unexpected spike in billing costs.

AWS Shield Standard is automatically enabled for all AWS customers at no additional cost. AWS Shield Advanced is an optional paid service.

Savings Plans is a flexible pricing model that offers low prices on Amazon EC2 instances, AWS Lambda, and AWS Fargate usage, in exchange for a commitment to a consistent amount of usage (measured in $/hour) for a 1 or 3 year term. Savings Plans is not applicable for the AWS Shield Advanced service.

----------------
# Amazon DataBase Migration svc comparision

* Use AWS Database Migration Service (AWS DMS) to replicate the data from the databases into Amazon Redshift
## AWS Database Migration Service
* helps you migrate databases to AWS quickly and securely. The source database remains fully operational during the migration, minimizing downtime to applications that rely on the database. With AWS Database Migration Service, you can continuously replicate your data with high availability and consolidate databases into a petabyte-scale data warehouse by streaming data to Amazon Redshift and Amazon S3.

Continuous Data Replication  via - https://aws.amazon.com/dms/

* You can migrate data to Amazon Redshift databases using AWS Database Migration Service. Amazon Redshift is a fully managed, petabyte-scale data warehouse service in the cloud. With an Amazon Redshift database as a target, you can migrate data from all of the other supported source databases.
* The Amazon Redshift cluster must be in the same AWS account and the same AWS Region as the replication instance. During a database migration to Amazon Redshift, AWS DMS first moves data to an Amazon S3 bucket. When the files reside in an Amazon S3 bucket, AWS DMS then transfers them to the proper tables in the Amazon Redshift data warehouse. AWS DMS creates the S3 bucket in the same AWS Region as the Amazon Redshift database. The AWS DMS replication instance must be located in that same region.


* Using AWS Glue to replicate the data from the databases into Amazon Redshift - AWS Glue is a fully managed extract, transform, and load (ETL) service that makes it easy for customers to prepare and load their data for analytics. AWS Glue job is meant to be used for batch ETL data processing.

* Using AWS Glue involves significant development efforts to write custom migration scripts to copy the database data into Redshift.

* Use AWS EMR to replicate the data from the databases into Amazon Redshift - Amazon EMR is the industry-leading cloud big data platform for processing vast amounts of data using open source tools such as Apache Spark, Apache Hive, Apache HBase, Apache Flink, Apache Hudi, and Presto. With EMR you can run Petabyte-scale analysis at less than half of the cost of traditional on-premises solutions and over 3x faster than standard Apache Spark. For short-running jobs, you can spin up and spin down clusters and pay per second for the instances used. For long-running workloads, you can create highly available clusters that automatically scale to meet demand. Amazon EMR uses Hadoop, an open-source framework, to distribute your data and processing across a resizable cluster of Amazon EC2 instances.
* Using EMR involves significant infrastructure management efforts to set up and maintain the EMR cluster. Additionally this option involves a major development effort to write custom migration jobs to copy the database data into Redshift.

* Use Amazon Kinesis Data Streams to replicate the data from the databases into Amazon Redshift - Amazon Kinesis Data Streams (KDS) is a massively scalable and durable real-time data streaming service. KDS can continuously capture gigabytes of data per second from hundreds of thousands of sources such as website clickstreams, database event streams, financial transactions, social media feeds, IT logs, and location-tracking events.

However, the user is expected to manually provision an appropriate number of shards to process the expected volume of the incoming data stream. The throughput of an Amazon Kinesis data stream is designed to scale without limits via increasing the number of shards within a data stream. Therefore Kinesis Data Streams is not the right fit for this use-case.

#### References:
* https://docs.aws.amazon.com/dms/latest/userguide/CHAP_Target.Redshift.html
* https://aws.amazon.com/dms/

# Vpc Endpoint Connecting services 

Amazon S3

Amazon DynamoDB
```
A VPC endpoint enables you to privately connect your VPC to supported AWS services and VPC endpoint services powered by AWS PrivateLink without requiring an internet gateway, NAT device, VPN connection, or AWS Direct Connect connection. Instances in your VPC do not require public IP addresses to communicate with resources in the service. Traffic between your VPC and the other service does not leave the Amazon network.

Endpoints are virtual devices. They are horizontally scaled, redundant, and highly available VPC components. They allow communication between instances in your VPC and services without imposing availability risks or bandwidth constraints on your network traffic.

There are two types of VPC endpoints: Interface Endpoints and Gateway Endpoints. An Interface Endpoint is an Elastic Network Interface with a private IP address from the IP address range of your subnet that serves as an entry point for traffic destined to a supported service.

A Gateway Endpoint is a gateway that you specify as a target for a route in your route table for traffic destined to a supported AWS service. The following AWS services are supported: Amazon S3 and Amazon DynamoDB.

You can use two types of VPC endpoints to access Amazon S3: gateway endpoints and interface endpoints. A gateway endpoint is a gateway that you specify in your route table to access Amazon S3 from your VPC over the AWS network. Interface endpoints extend the functionality of gateway endpoints by using private IP addresses to route requests to Amazon S3 from within your VPC, on premises, or from a VPC in another AWS Region using VPC peering or AWS Transit Gateway.

You must remember that these two services use a VPC gateway endpoint. The rest of the AWS services use VPC interface endpoints.
```
Gateway VPC endpoints:
<img width="2424" height="1754" alt="image" src="https://github.com/user-attachments/assets/392b1bc6-3929-478d-acc3-c272d83e6ce5" />

----------------

# Lambda 

By default, AWS Lambda functions always operate from an AWS-owned VPC and hence have access to any public internet address or public AWS APIs. Once an AWS Lambda function is VPC-enabled, it will need a route through a Network Address Translation gateway (NAT gateway) in a public subnet to access public resources

AWS Lambda functions always operate from an AWS-owned VPC. By default, your function has the full ability to make network requests to any public internet address — this includes access to any of the public AWS APIs. For example, your function can interact with AWS DynamoDB APIs to PutItem or Query for records. You should only enable your functions for VPC access when you need to interact with a private resource located in a private subnet. An Amazon RDS instance is a good example.

Once your function is VPC-enabled, all network traffic from your function is subject to the routing rules of your VPC/Subnet. If your function needs to interact with a public resource, you will need a route through a NAT gateway in a public subnet.

When to VPC-Enable an AWS Lambda Function:  via - https://aws.amazon.com/blogs/architecture/best-practices-for-developing-on-aws-lambda/

Since AWS Lambda functions can scale extremely quickly, it's a good idea to deploy a Amazon CloudWatch Alarm that notifies your team when function metrics such as ConcurrentExecutions or Invocations exceeds the expected threshold

Since AWS Lambda functions can scale extremely quickly, this means you should have controls in place to notify you when you have a spike in concurrency. A good idea is to deploy an Amazon CloudWatch Alarm that notifies your team when function metrics such as ConcurrentExecutions or Invocations exceeds your threshold. You should create an AWS Budget so you can monitor costs on a daily basis.

If you intend to reuse code in more than one AWS Lambda function, you should consider creating an AWS Lambda Layer for the reusable code

You can configure your AWS Lambda function to pull in additional code and content in the form of layers. A layer is a ZIP archive that contains libraries, a custom runtime, or other dependencies. With layers, you can use libraries in your function without needing to include them in your deployment package. Layers let you keep your deployment package small, which makes development easier. A function can use up to 5 layers at a time.

You can create layers, or use layers published by AWS and other AWS customers. Layers support resource-based policies for granting layer usage permissions to specific AWS accounts, AWS Organizations, or all accounts. The total unzipped size of the function and all layers can't exceed the unzipped deployment package size limit of 250 megabytes.

<img width="823" height="628" alt="image" src="https://github.com/user-attachments/assets/a503f9dd-a176-458a-a6c1-fd7cea3aa392" />

----------


Below is a compact “book blueprint” written in original wording and structured so you can explore each section as a chapter.

***

## Services structure and strategy

Each service is organized around three pillars:

- **Exam domains**: Map chapters to SAA‑C03 and DVA‑C02 domains (secure, resilient, high‑performance, cost‑optimized, development, deployment, troubleshooting).[2][1]
- **Service families**: Within each domain, group by Compute, Storage, Database, Networking, Security, Integration, Observability, and Migration.[3]
- **Scenario patterns**: End every major section with “If the question says X, think of Y service”, emphasizing tradeoffs and USPs.

Use AWS official exam guides as your primary scope control:

- SAA‑C03 exam guide for architect topics and in‑scope services.[1]
- DVA‑C02 exam guide for developer‑centric services (API Gateway, Lambda, Step Functions, Cognito, Code* tools, etc.).[4][2]

For each service chapter, keep a fixed structure:

1. What the service is.  
2. Core capabilities and USPs.  
3. When to use vs main alternatives (decision patterns).  
4. Common exam traps and limits.  
5. 2–3 short scenario Q&A snippets.

Cite AWS docs and whitepapers as you build the full book (for example, “Amazon DynamoDB Developer Guide”, “AWS Well‑Architected Framework”, “AWS Security Best Practices”, “AWS Storage Services Overview”).[3]

Below is the extended description for the services you explicitly listed, with exam‑oriented “when to use” guidance.

***

## AWS Config

AWS Config is a **configuration recording and compliance evaluation** service for AWS resources. It continuously records configuration changes (resource properties and relationships) and evaluates them against rules.[5]

Key points and USPs:

- Records configuration history for supported resources, including relationships like which security group is attached to which ENI.[5]
- Lets you define rules (managed or custom) that check compliance, for example “GuardDuty must be enabled in this account and Region”.[5]
- Integrates well with Security Hub and Organizations for multi‑account governance.

When to use:

- Need to answer “what changed and when?” for security audits or troubleshooting.  
- Need continuous compliance checking (CIS, PCI, internal policies) across accounts.  
- Need resource inventory and drift detection beyond CloudFormation.

Typical use cases:

- Ensuring all S3 buckets have encryption enabled; non‑compliant buckets are flagged.  
- Verifying all VPCs enforce specific network ACL patterns.  
- Checking that GuardDuty, Macie, or Security Hub are enabled in all member accounts.[5]

***

## Amazon GuardDuty

Amazon GuardDuty is a **managed threat detection** service that analyzes AWS data sources for suspicious activity.[6]

Key capabilities:

- Monitors CloudTrail events, VPC Flow Logs, and DNS logs to detect anomalies and known attack techniques.[6]
- Extended Threat Detection correlates multi‑stage attacks over time and across resources.[6]
- Generates findings with severity levels and recommended remediation.

When to use:

- Need continuous, managed detection of compromised IAM keys, unusual API calls, or data exfiltration attempts.  
- Want security intelligence without running your own SIEM or ML models.

Typical use cases:

- Detecting an IAM user making API calls from unusual geolocations.  
- Identifying EC2 instances communicating with known malicious IPs.  
- Centralizing threat detection for an AWS Organizations multi‑account setup.

***

## Amazon Macie

Amazon Macie is a **data security and privacy service** that uses ML and pattern matching to discover and protect sensitive data in Amazon S3.[7]

Key capabilities:

- Automatically classifies data such as PII, financial data, and credentials in S3.[7]
- Flags publicly accessible buckets and objects containing sensitive data.  
- Integrates with Security Hub and EventBridge for alerting and remediation workflows.[7]

When to use:

- Regulatory‑driven workloads (GDPR, HIPAA, PCI‑DSS) where you need to know where sensitive data resides.  
- Environments with many S3 buckets and teams where misconfigurations are likely.

Typical use cases:

- Scanning all S3 buckets to identify files with PII stored in unintended locations.  
- Detecting buckets that suddenly become public and contain customer data.  
- Feeding Macie findings into automated remediation Lambdas through EventBridge.

***

## Amazon DynamoDB and DAX

DynamoDB is a **fully managed NoSQL key‑value and document database** designed for single‑digit millisecond performance at virtually any scale.[8]

DynamoDB USPs:

- Serverless capacity modes (on‑demand and provisioned with auto scaling).  
- Global tables for multi‑Region active‑active workloads.  
- Fine‑grained security with IAM, encryption at rest, and point‑in‑time recovery.

DynamoDB Accelerator (DAX) is a **fully managed in‑memory cache** for DynamoDB that provides microsecond read latency.[9]

DAX key characteristics:

- Sits in front of DynamoDB, caching read‑heavy workloads with eventual consistency by default.[9]
- Exposed via a DynamoDB‑compatible client, so application changes are minimal.[9]
- Access control is handled through an IAM service role associated with the DAX cluster, and users inherit its permissions when going through the cluster.[10]

When to use DynamoDB:

- Need massive scale with predictable low latency and flexible schema.  
- Workloads favor primary‑key access patterns and require high availability.

When to add DAX:

- Read‑heavy workloads with repeated reads of the same items.  
- Performance‑sensitive APIs that must reduce request units and latency.[9]

Typical use cases:

- Session store for highly scalable web apps.  
- Gaming leaderboards requiring high write and read throughput.  
- High‑traffic product catalogs using DAX to offload reads and reduce DynamoDB costs.

***

## Site‑to‑Site VPN

AWS Site‑to‑Site VPN provides **IPsec tunnels between your on‑premises network and an AWS VPC**.[3]

Key characteristics:

- Managed VPN endpoints on AWS side (Virtual Private Gateway or Transit Gateway).  
- Two tunnels per connection for high availability.  
- Encrypted traffic over the public internet.

When to use:

- Need secure connectivity between on‑premises and AWS without dedicated physical circuits.  
- Backup path for Direct Connect to maintain hybrid connectivity.

Typical use cases:

- Hybrid applications where app servers run in AWS but databases remain on‑premises.  
- Gradual migrations where traffic shifts from on‑prem to AWS over time.  
- DR scenarios where AWS hosts standby workloads reachable over VPN.

***

## Amazon FSx and FSx for Lustre

Amazon FSx is a **family of managed file systems** for specific workloads (Windows, Lustre, NetApp ONTAP, OpenZFS).[8]

FSx for Lustre:

- High‑performance, POSIX‑compliant file system optimized for HPC and big data.  
- Integrates with S3 by importing and exporting objects, mapping them to files in Lustre.[8]

USPs:

- Very high throughput and low latency for parallel workloads such as ML training, seismic processing, or financial simulations.  
- Seamless data lifecycle with S3 as the durable data lake and Lustre as the compute‑attached cache.

When to use:

- When you need HPC‑grade performance with shared storage for many EC2 instances.  
- When you run analytics or ML workloads on data primarily stored in S3 but need POSIX access.

Typical use cases:

- Training ML models on large image or log datasets stored in S3.  
- Rendering farms needing fast shared access to assets and frames.

***

## AWS Shield and Shield Advanced

AWS Shield is a **managed DDoS protection service** for applications running on AWS.[8]

Two tiers:

- Standard: Automatically included for all customers, protects against most common L3/L4 attacks on services like CloudFront, Route 53, and ALB.[8]
- Shield Advanced: Paid tier with enhanced protections, detection, and response.[8]

Shield Advanced USPs:

- Advanced detection and mitigation for larger, more sophisticated DDoS attacks.  
- Cost protection against scaling charges during approved DDoS events on certain services.  
- 24x7 access to the AWS DDoS Response Team (DRT).[8]

Pricing aspects (conceptual for the book):

- Monthly subscription per protected resource or account, plus possible usage‑based elements, varying by resource type.[8]
- Readers should consult the “AWS Shield Pricing” page for current numbers.

When to use:

- Critical public‑facing workloads where downtime or DDoS risk is unacceptable.  
- Enterprises needing SLA‑backed DDoS support and cost protection.

Typical use cases:

- High‑visibility consumer web applications fronted by CloudFront and ALB.  
- Financial or gaming workloads that are frequent DDoS targets.

***

## Amazon ElastiCache

Amazon ElastiCache is a **managed in‑memory data store** compatible with Redis and Memcached.[8]

Key capabilities:

- Sub‑millisecond latency for frequently accessed data.  
- Supports features like replication, clustering, and persistence (Redis).  
- Integrates tightly with VPC, IAM, and CloudWatch.

USPs:

- Simplifies operating Redis/Memcached clusters at scale.  
- Reduces load on databases like RDS or DynamoDB by caching hot data.[8]

When to use:

- Application needs shared, low‑latency caching or session storage.  
- Want to offload expensive read queries from RDS or other backends.

Typical use cases:

- Caching query results from RDS or Aurora.  
- Storing web session state for horizontally scaled app servers.  
- Leaderboards or counters that require very fast increments.

***

## Amazon VPC and VPC endpoints

Amazon VPC is a **logically isolated virtual network** in AWS where you define subnets, route tables, and gateways.[3]

Key concepts:

- Public and private subnets with route tables controlling traffic paths.  
- Internet Gateway, NAT Gateway, Transit Gateway for external connectivity.  
- Security groups and network ACLs for network‑level access control.

VPC endpoints:

- Provide **private connectivity** from a VPC to AWS services without using the public internet.[3]
- Two main types: Interface endpoints (powered by PrivateLink) and Gateway endpoints (S3, DynamoDB).[3]

USPs:

- Reduce attack surface by avoiding public endpoints.  
- Improve performance and reliability for service access.  
- Simplify firewall rules, as traffic stays inside AWS network.

When to use:

- Need to access S3 or DynamoDB from private subnets without a NAT Gateway.  
- Need private connectivity to services like API Gateway, SQS, SNS, or custom partner services.

Typical use cases:

- Private microservices architectures where all inter‑service and AWS service calls remain within VPC.  
- Regulated environments where egress to the public internet is heavily restricted.

***

## AWS Snow Family

The AWS Snow Family consists of **physical devices for data migration and edge computing**.

Key members (conceptual view):

- Devices ranging from portable units to rack‑mounted edge computing appliances.  
- Designed for environments with limited or no reliable network connectivity.[3]

USPs:

- Move many terabytes or petabytes of data into or out of AWS without long network transfer times.  
- Run compute and storage at the edge and later synchronize to AWS.

When to use:

- Large‑scale migrations from data centers where network bandwidth is limited.  
- Edge sites such as ships, remote plants, or disconnected locations.

Typical use cases:

- Bulk video or log dataset ingestion into S3.  
- Edge analytics and ML inference with periodic synchronization to the cloud.

***

## Launch Templates

Launch Templates define **versioned configuration for EC2 instances**, including all parameters needed to launch or scale instances.[8]

Key capabilities:

- Store AMI, instance type, key pair, security groups, network interfaces, user data, and advanced options (spot options, capacity reservations).  
- Support versioning so Auto Scaling groups or Spot Fleets can reference specific or latest versions.[8]

USPs:

- Reusability and consistency across Auto Scaling groups and manual launches.  
- Fine‑grained control over mixed instances policies and advanced networking.

When to use:

- Whenever configuring an Auto Scaling group or needing repeatable EC2 configuration.  
- When using Spot Instances with sophisticated allocation strategies.

Typical use cases:

- Blue/green or rolling deployments by updating template versions.  
- Standardized golden image pattern for a fleet of microservices.

***

## AWS Lambda

AWS Lambda is a **serverless compute service** that runs code in response to events without managing servers.[8]

Key characteristics:

- Pay per invocation and execution time, with automatic scaling.  
- Integrates with many AWS services as event sources (API Gateway, S3, DynamoDB, EventBridge, Kinesis, etc.).[8]
- Supports multiple runtimes and container images.

USPs:

- Eliminates server management for event‑driven and microservice workloads.  
- Scales automatically with demand, ideal for spiky traffic.  
- Fine‑grained cost transparency aligned with actual usage.

When to use:

- Stateless request processing, lightweight APIs, and glue logic between services.  
- Backends for mobile/web apps, streaming processing, or cron‑like jobs.

Typical use cases:

- S3 upload triggers to process images or logs.  
- API Gateway + Lambda REST APIs for serverless backend.  
- EventBridge‑driven automation tasks across accounts.

***

## AWS Database Migration Service (DMS)

AWS DMS is a **managed replication and migration service** for moving databases to, from, or within AWS.[8]

Key capabilities:

- Supports homogeneous and heterogeneous migrations (e.g., Oracle to Aurora).  
- Can perform one‑time migrations plus ongoing CDC (change data capture) for minimal downtime.[8]
- Works with many engines: RDS, Aurora, on‑premises databases, and some cloud‑hosted engines.

USPs:

- Low‑downtime migrations with continuous replication until cutover.  
- Handles both schema and data with helpers like the Schema Conversion Tool for heterogeneous moves.

When to use:

- Migrating existing on‑premises or EC2‑hosted databases to RDS or Aurora.  
- Consolidating multiple databases into a central data warehouse.  
- Real‑time replication pipelines where source must remain operational.

Typical use cases:

- Lift‑and‑shift Oracle to Amazon Aurora PostgreSQL with minimal downtime.  
- Continuous replication from on‑prem MySQL to Aurora for phased migration.

***

## Amazon Redshift

Amazon Redshift is a **fully managed, petabyte‑scale data warehouse** for analytics workloads.[8]

Key characteristics:

- Columnar storage, massively parallel processing, and SQL interface compatible with many BI tools.  
- Redshift Spectrum enables querying data directly in S3.  
- Integrates with Glue, S3, and Kinesis for data ingestion and transformation.

USPs:

- Optimized for analytical queries over large datasets with high concurrency.  
- Can act as the central warehouse in a lake‑house architecture using S3 as the data lake.[8]

When to use:

- Complex BI and analytics workloads requiring fast aggregations over large fact tables.  
- Centralized reporting across data sources like RDS, DynamoDB (via export), and log data in S3.

Typical use cases:

- Business intelligence dashboards for sales, marketing, and operations.  
- Clickstream and event analytics over billions of rows.  
- Consolidation of OLTP exports from multiple systems into a single analytical store.

***
--------------
# References

* [Solution architect exam guide ](https://docs.aws.amazon.com/aws-certification/latest/examguides/solutions-architect-associate-03.html)
* [Developer Associate Exam Guide ](https://docs.aws.amazon.com/aws-certification/latest/examguides/developer-associate-02.html)
* [KodeKloud SA guide ](https://kodekloud.com/blog/aws-solution-architect-guide/)
* [Cloud Engineer Skilss DA Guide ](https://cloudengineerskills.com/posts/aws-developer-associate/)
* [Amazon GuardDuty Docs](https://docs.aws.amazon.com/config/latest/developerguide/guardduty-enabled-centralized.html)
* [Amazon GuardDuty Docs Setting](https://docs.aws.amazon.com/guardduty/latest/ug/guardduty_settingup.html)
* [AWS security Hub (https://docs.aws.amazon.com/securityhub/latest/userguide/fsbp-standard.html)
* [tutorials dojo](https://tutorialsdojo.com/aws-certified-solutions-architect-associate-saa-c03/)
* [AWS dynamodb dax dev guide](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/DAX.concepts.html)
* [DAX access control guide](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/DAX.access-control.html)
* [AWS exam guide](https://docs.aws.amazon.com/pdfs/aws-certification/latest/examguides/aws-certification-exam-guides.pdf)
* [SAA cheat sheet](https://digitalcloud.training/category/aws-cheat-sheets/aws-solutions-architect-associate/)
* [SAA blue print](https://www.pluralsight.com/resources/blog/cloud/aws-solutions-architect-associate-exam-blueprint-6-areas-to-master)
[WhizLabs blog](https://www.whizlabs.com/blog/aws-services-aws-developer-associate-exam/)
* [AWS imp Topics for SAA reddit](https://www.reddit.com/r/AWSCertifications/comments/qznczk/important_topics_for_aws_solutions_architect/)
* [AWS SAA study guide](https://dev.to/dietertroy/aws-certified-solutions-architect-associate-study-guide-38c2)
* [DVCA cheat sheet](https://digitalcloud.training/category/aws-cheat-sheets/aws-developer-associate/)
* [Reddit Link for AWS SAA](https://www.reddit.com/r/AWSCertifications/comments/175zyam/this_is_for_aws_solution_architect_associate_exam/)
* [Redit Link for DVCA topics](https://www.reddit.com/r/AWSCertifications/comments/16s7x4i/aws_developer_associate_dvac02_exam_topics_and/)
* [AWS SA Exam guide](https://www.slideshare.net/slideshow/aws-certified-solutions-architect-associate-exam-guide-pdf/265038165)
