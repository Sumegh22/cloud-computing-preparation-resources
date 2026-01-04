# AWS Cognito
* Cognito User Pools Authorises api calls within api gateway.
*  Cognito identity pools provide aws credentials to users to access aws resources.
  
# S3 Bucket data
* To setup a one time copy of S3 bucket data from one region to another region You can use Aws snowball, Use S3 Sync command, or Setup S3 batch replication to copy objects across S3 buckets in another Region using S3 console and delete replication configuration.

# Aws Kinesis 
* Use aws kinesis data streams to process stream data in near real time.

# AWS Rds and Databases 
1. Use read replica to significantly reduce load on db.

# AWS NFS to EFS DataSync

``` 
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
```

# Rds for Postgres and Mysql (Latency even with Read replicas)
```
* Use Amazon Aurora Global Database to enable fast local reads with low latency in each region

* Amazon Aurora is a MySQL and PostgreSQL-compatible relational database built for the cloud, that combines the performance and availability of traditional enterprise databases with the simplicity and cost-effectiveness of open source databases. Amazon Aurora features a distributed, fault-tolerant, self-healing storage system that auto-scales up to 64TB per database instance. Aurora is not an in-memory database.

* Amazon Aurora Global Database is designed for globally distributed applications, allowing a single Amazon Aurora database to span multiple AWS regions. It replicates your data with no impact on database performance, enables fast local reads with low latency in each region, and provides disaster recovery from region-wide outages. Amazon Aurora Global Database is the correct choice for the given use-case.


* Amazon Aurora Global Database Features:  via - https://aws.amazon.com/rds/aurora/global-database/
```

# Ec2 application behind and ASG
* To make it more resilient and reduce load on app
```
You can use Amazon Aurora replicas and Amazon CloudFront distribution to make the application more resilient to spikes in request rates.

Use Amazon Aurora Replica

* Amazon Aurora Replicas have two main purposes. You can issue queries to them to scale the read operations for your application. You typically do so by connecting to the reader endpoint of the cluster. That way, Aurora can spread the load for read-only connections across as many Aurora Replicas as you have in the cluster. Amazon Aurora Replicas also help to increase availability. If the writer instance in a cluster becomes unavailable, Aurora automatically promotes one of the reader instances to take its place as the new writer. Up to 15 Aurora Replicas can be distributed across the Availability Zones (AZs) that a DB cluster spans within an AWS Region.

* Use Amazon CloudFront distribution in front of the Application Load Balancer

* Amazon CloudFront is a fast content delivery network (CDN) service that securely delivers data, videos, applications, and APIs to customers globally with low latency, high transfer speeds, all within a developer-friendly environment. CloudFront points of presence (POPs) (edge locations) make sure that popular content can be served quickly to your viewers. Amazon CloudFront also has regional edge caches that bring more of your content closer to your viewers, even when the content is not popular enough to stay at a POP, to help improve performance for that content.

* Amazon CloudFront offers an origin failover feature to help support your data resiliency needs. Amazon CloudFront is a global service that delivers your content through a worldwide network of data centers called edge locations or points of presence (POPs). If your content is not already cached in an edge location, Amazon CloudFront retrieves it from an origin that you've identified as the source for the definitive version of the content.

```

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




