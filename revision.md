1. Cognito User Pools Authorises api calls within api gateway.
2. Cognito identity pools provide aws credentials to users to access aws resources.
3. To setup a one time copy of S3 bucket data from one region to another region You can use Aws snowball, Use S3 Sync command, or Setup S3 batch replication to copy objects across S3 buckets in another Region using S3 console and delete replication configuration.
4. Use aws kinesis data streams to process stream data in near real time.
5. read replica and significantly reduce db bw.

6. # AWS NFS to EFS DataSync

``` 
* Configure an AWS DataSync agent on the on-premises server that has access to the NFS file system. Transfer data over the AWS Direct Connect connection to an AWS PrivateLink interface VPC endpoint for Amazon EFS by using a private VIF. Set up an AWS DataSync scheduled task to send the video files to the Amazon EFS file system every 24 hours

* AWS DataSync is an online data transfer service that simplifies, automates, and accelerates copying large amounts of data between on-premises storage systems and  AWS Storage services, as well as between AWS Storage services.

* You can use AWS DataSync to migrate data located on-premises, at the edge, or in other clouds to Amazon S3, Amazon EFS, Amazon FSx for Windows File Server, Amazon FSx for Lustre, Amazon FSx for OpenZFS, and Amazon FSx for NetApp ONTAP.

* AWS DataSync:  
<img width="2360" height="1394" alt="image" src="https://github.com/user-attachments/assets/4959ddda-58c4-441f-8f37-265fc45f759d" />

via - https://aws.amazon.com/datasync/

* To establish a private connection between your virtual private cloud (VPC) and the Amazon EFS API, you can create an interface VPC endpoint. You can also access the interface VPC endpoint from on-premises environments or other VPCs using AWS VPN, AWS Direct Connect, or VPC peering.

* AWS Direct Connect provides three types of virtual interfaces: public, private, and transit.

* AWS Direct Connect VIFs:  via - https://aws.amazon.com/premiumsupport/knowledge-center/public-private-interface-dx/

* For the given use case, you can send data over the Direct Connect connection to an AWS PrivateLink interface VPC endpoint for Amazon EFS by using a private VIF.

* Using task scheduling in AWS DataSync, you can periodically execute a transfer task from your source storage system to the destination. You can use the DataSync scheduled task to send the video files to the Amazon EFS file system every 24 hours.
```

7. # Rds for Postgres and Mysql (Latency even with Read replicas)
```
* Use Amazon Aurora Global Database to enable fast local reads with low latency in each region

* Amazon Aurora is a MySQL and PostgreSQL-compatible relational database built for the cloud, that combines the performance and availability of traditional enterprise databases with the simplicity and cost-effectiveness of open source databases. Amazon Aurora features a distributed, fault-tolerant, self-healing storage system that auto-scales up to 64TB per database instance. Aurora is not an in-memory database.

* Amazon Aurora Global Database is designed for globally distributed applications, allowing a single Amazon Aurora database to span multiple AWS regions. It replicates your data with no impact on database performance, enables fast local reads with low latency in each region, and provides disaster recovery from region-wide outages. Amazon Aurora Global Database is the correct choice for the given use-case.

<img width="2417" height="691" alt="image" src="https://github.com/user-attachments/assets/cd1ec067-09ce-46ac-b1c3-4ef2f12ba70f" />


* Amazon Aurora Global Database Features:  via - https://aws.amazon.com/rds/aurora/global-database/
```
