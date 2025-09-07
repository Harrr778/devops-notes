#  Amazon S3 Storage Classes

## Overview

Amazon S3 offers a range of storage classes that you can choose from based on the performance, data access, resiliency, and cost requirements of your workloads. S3 storage classes are purpose-built to provide the lowest cost storage for different access patterns. S3 storage classes are ideal for virtually any use case, including those with demanding performance needs, data lakes, data residency requirements, unknown or changing access patterns, or archival storage.

The S3 storage classes include **S3 Intelligent-Tiering** for automatic cost savings for data with unknown or changing access patterns, **S3 Standard** for frequently accessed data, **S3 Express One Zone** for your most frequently accessed data, **S3 Standard-Infrequent Access (S3 Standard-IA)** and **S3 One Zone-Infrequent Access (S3 One Zone-IA)** for less frequently accessed data, **S3 Glacier Instant Retrieval** for archive data that needs immediate access, **S3 Glacier Flexible Retrieval (formerly S3 Glacier)** for rarely accessed long-term data that does not require immediate access, and **Amazon S3 Glacier Deep Archive (S3 Glacier Deep Archive)** for long-term archive and digital preservation with retrieval in hours at the lowest cost storage in the cloud.

Amazon S3 provides the most durable storage in the cloud. Based on its unique architecture, S3 is designed to exceed 99.999999999% (11 nines) data durability. Additionally, S3 stores data redundantly across a minimum of 3 Availability Zones by default, providing built-in resilience against widespread disaster. Customers can store data in a single AZ to minimize storage cost or latency, in multiple AZs for resilience against the permanent loss of an entire data center, or in multiple AWS Regions to meet geographic resilience requirements. If you have data residency requirements that can’t be met by an existing AWS Region, you can use S3 storage classes for AWS Dedicated Local Zones or S3 on Outposts racks to store your data in a specific data perimeter. 

You can configure S3 storage classes at the object level, and a single general purpose bucket can contain objects stored across all storage classes except S3 Express One Zone. Amazon S3 also offers capabilities to manage your data throughout its lifecycle. Once an S3 Lifecycle policy is set, your data will automatically transfer to a different storage class without any changes to your application. S3 directory buckets only allow objects stored in the S3 Express One Zone storage class, which provides faster data processing within a single Availability Zone, and do not support S3 Lifecycle transitions.

[View the Amazon S3 storage classes overview infographic.](https://aws.amazon.com/s3/storage-classes-infographic/)

## General purpose

### Amazon S3 Standard (S3 Standard)

S3 Standard offers high durability, availability, and performance object storage for frequently accessed data. Because it delivers low latency and high throughput, S3 Standard is appropriate for a wide variety of use cases, including cloud applications, dynamic websites, content distribution, mobile and gaming applications, and big data analytics. 

**Key features:**

- General purpose storage for frequently accessed data
- Low latency and high throughput performance
- Designed to deliver 99.99% availability with an [availability SLA](https://aws.amazon.com/s3/sla/) of 99.9%

## Unknown or changing access

### Amazon S3 Intelligent-Tiering (S3 Intelligent-Tiering)

[**Amazon S3 Intelligent-Tiering (S3 Intelligent-Tiering)**](https://aws.amazon.com/s3/storage-classes/intelligent-tiering/) is the first cloud storage that automatically reduces your storage costs on a granular object level by automatically moving data to the most cost-effective access tier based on access frequency, without performance impact, retrieval fees, or operational overhead. S3 Intelligent-Tiering delivers milliseconds latency and high throughput performance for frequently, infrequently, and rarely accessed data in the Frequent, Infrequent, and Archive Instant Access tiers. You can use S3 Intelligent-Tiering as the default storage class for virtually any workload, especially data lakes, data analytics, new applications, and user-generated content.

For a small monthly object monitoring and automation charge, S3 Intelligent-Tiering monitors access patterns and automatically moves objects that have not been accessed to lower-cost access tiers. S3 Intelligent-Tiering automatically stores objects in three access tiers: one tier that is optimized for frequent access, a 40% lower-cost tier that is optimized for infrequent access, and a 68% lower-cost tier optimized for rarely accessed data. S3 Intelligent-Tiering monitors access patterns and moves objects that have not been accessed for 30 consecutive days to the Infrequent Access tier and after 90 days of no access to the Archive Instant Access tier. For data that does not require immediate retrieval, you can set up S3 Intelligent-Tiering to monitor and automatically move objects that aren’t accessed for 180 days or more to the Deep Archive Access tier to realize up to 95% in storage cost savings.

There are no retrieval charges in S3 Intelligent-Tiering. If an object in the Infrequent or Archive Instant Access tier is accessed later, it’s automatically moved back to the Frequent Access tier. If the object you’re retrieving is stored in the optional Deep Archive tiers, before you can retrieve the object, you must first restore a copy using RestoreObject.  For information about restoring archived objects, see [Restoring Archived Objects](https://docs.aws.amazon.com/AmazonS3/latest/userguide/restoring-objects.html). No additional tiering charges apply when objects are moved between access tiers within the S3 Intelligent-Tiering storage class.

**Key features:**

- Automatic cost savings for data with unknown or changing access patterns
- Frequent, Infrequent, and Archive Instant Access tiers have the same low-latency and high-throughput performance of S3 Standard
- The Infrequent Access tier saves up to 40% on storage costs
- The Archive Instant Access tier saves up to 68% on storage costs
- Opt-in asynchronous archive capabilities for objects that become rarely accessed
- Deep Archive Access tier has the same performance as Glacier Deep Archive and saves up to 95% for rarely accessed objects
- Designed to deliver 99.9% availability with an [availability SLA](https://aws.amazon.com/s3/sla/) of 99%
- Small monthly monitoring and automation charge
- No operational overhead, no lifecycle charges, no retrieval charges, and no minimum storage duration
- Objects smaller than 128KB can be stored in S3 Intelligent-Tiering but will always be charged at the Frequent Access tier rates, and are not charged the monitoring and automation charge.

## High performance

### Amazon S3 Express One Zone

[**Amazon S3 Express One Zone**](https://aws.amazon.com/s3/storage-classes/express-one-zone/) is a high-performance, single-Availability Zone storage class purpose-built to deliver consistent single-digit millisecond data access for your most frequently accessed data and latency-sensitive applications. S3 Express One Zone can improve data access speeds by 10x and reduce request costs by 50% compared to S3 Standard. While you have always been able to choose a specific AWS Region to store your S3 data, with S3 Express One Zone you can select a specific AWS Availability Zone within an AWS Region to store your data. You can choose to co-locate your storage and compute resources in the same Availability Zone to further optimize performance, which helps lower compute costs and run workloads faster. With S3 Express One Zone, data is stored in a different bucket type—an Amazon S3 directory bucket—which supports hundreds of thousands of requests per second. Additionally, you can use S3 Express One Zone with services such as [Amazon SageMaker Model Training](https://aws.amazon.com/sagemaker/train/), [Amazon Athena](https://aws.amazon.com/athena/), [Amazon EMR](https://aws.amazon.com/emr/), and [AWS Glue](https://aws.amazon.com/glue/) Data Catalog to accelerate your ML and analytics workloads. With S3 Express One Zone, storage automatically scales up or down based on your consumption and need, and you no longer need to manage multiple storage systems for low-latency workloads.

**Key features:**

- High performance storage for your most frequently accessed data
- Consistent single-digit millisecond request latency
- Improve access speeds by 10x and reduce request costs by 50% compared to S3 Standard
- Select an AWS Availability Zone and have the option to co-locate storage and compute resources for even lower latency, with reduced processing time and more efficient use of compute resources contributing to lower overall total cost of ownership
- Accelerate analytics and ML workloads with AWS service integrations
- Scale to handle millions of requests per minute
- Optimized for large datasets with many small objects
- Use existing Amazon S3 APIs with different bucket type – directory buckets
- Designed to deliver 99.95% availability with an [availability SLA](https://aws.amazon.com/s3/sla/) of 99.9%


## Infrequent access

### Amazon S3 Standard-Infrequent Access (S3 Standard-IA)

S3 Standard-IA is for data that is accessed less frequently, but requires rapid access when needed. S3 Standard-IA offers the high durability, high throughput, and low latency of S3 Standard, with a low per GB storage price and per GB retrieval charge. This combination of low cost and high performance make S3 Standard-IA ideal for long-term storage, backups, and as a data store for disaster recovery files. You can configure S3 storage classes at the object level, and a single bucket can contain objects stored across S3 Standard, S3 Intelligent-Tiering, S3 Standard-IA, and S3 One Zone-IA. You can also use S3 Lifecycle policies to automatically transition objects between storage classes without any application changes.

**Key features:**

- Infrequently accessed data that needs millisecond access
- Same low latency and high throughput performance of S3 Standard
- Designed to deliver 99.9% availability with an [availability SLA](https://aws.amazon.com/s3/sla/) of 99%

### Amazon S3 One Zone-Infrequent Access (S3 One Zone-IA)

S3 One Zone-IA is for data that is accessed less frequently, but requires rapid access when needed. Unlike other S3 Storage Classes which store data in a minimum of three Availability Zones (AZs), S3 One Zone-IA stores data in a single AZ and costs 20% less than S3 Standard-IA. S3 One Zone-IA is ideal for customers who want a lower-cost option for infrequently accessed data but do not require the availability and resilience of S3 Standard or S3 Standard-IA. It’s a good choice for storing secondary backup copies of on-premises data or easily re-creatable data. You can also use it as cost-effective storage for data that is replicated from another AWS Region using S3 Cross-Region Replication.

S3 One Zone-IA offers the same high throughput, and low latency of S3 Standard, with a low per GB storage price and per GB retrieval charge. Using similar engineering designs as S3 Regional storage classes, S3 One Zone-IA also offers 11 nines of durability, but may be susceptible to data loss in the unlikely case of the loss or damage to all or part of an AWS Availability Zone. You can configure S3 storage classes at the object level, and a single general purpose bucket can contain objects stored across all storage classes except S3 Express One Zone. You can also use S3 Lifecycle policies to automatically transition objects between storage classes without any application changes.

Key features:

- Re-creatable infrequently accessed data
- Same low latency and high throughput performance of S3 Standard
- Designed to deliver 99.5% availability with an availability SLA of 99%

## Archive

### Overview

The [**Amazon S3 Glacier storage classes**](https://aws.amazon.com/s3/storage-classes/glacier/) are purpose-built for data archiving, and are designed to provide you with the highest performance, the most retrieval flexibility, and the lowest cost archive storage in the cloud. You can choose from three archive storage classes optimized for different access patterns and storage duration. For archive data that needs immediate access, such as medical images, news media assets, or genomics data, choose the S3 Glacier Instant Retrieval storage class, an archive storage class that delivers the lowest cost storage with milliseconds retrieval. For archive data that does not require immediate access but needs the flexibility to retrieve large sets of data at no cost, such as backup or disaster recovery use cases, choose S3 Glacier Flexible Retrieval (formerly S3 Glacier), with retrieval in minutes or free bulk retrievals in 5—12 hours. To save even more on long-lived archive storage such as compliance archives and digital media preservation, choose S3 Glacier Deep Archive, the lowest cost storage in the cloud with data retrieval from 12—48 hours.

### Amazon S3 Glacier Instant Retrieval

Amazon S3 Glacier Instant Retrieval is an archive storage class that delivers the lowest-cost storage for long-lived data that is rarely accessed and requires retrieval in milliseconds. With S3 Glacier Instant Retrieval, you can save up to 68% on storage costs compared to using the S3 Standard-Infrequent Access (S3 Standard-IA) storage class, when your data is accessed once per quarter. S3 Glacier Instant Retrieval delivers the fastest access to archive storage, with the same throughput and milliseconds access as the S3 Standard and S3 Standard-IA storage classes. S3 Glacier Instant Retrieval is ideal for archive data that needs immediate access, such as medical images, news media assets, or user-generated content archives. You can upload objects directly to S3 Glacier Instant Retrieval, or use S3 Lifecycle policies to transfer data from the S3 storage classes. For more information, visit the [**Amazon S3 Glacier Instant Retrieval page »**](https://aws.amazon.com/s3/storage-classes/glacier/instant-retrieval/)

**Key features:**

- Long-lived data that is accessed a few times per year with instant retrievals
- Data retrieval in milliseconds with the same performance as S3 Standard
- Designed to deliver 99.9% availability with an [availability SLA](https://aws.amazon.com/s3/sla/) of 99%
- 128 KB minimum object size
- S3 PUT API for direct uploads to S3 Glacier Instant Retrieval, and S3 Lifecycle management for automatic migration of objects

### Amazon S3 Glacier Flexible Retrieval (Formerly S3 Glacier)

S3 Glacier Flexible Retrieval delivers low-cost storage, up to 10% lower cost (than S3 Glacier Instant Retrieval), for archive data that is accessed 1—2 times per year and is retrieved asynchronously. For archive data that does not require immediate access but needs the flexibility to retrieve large sets of data at no cost, such as backup or disaster recovery use cases, S3 Glacier Flexible Retrieval (formerly S3 Glacier) is the ideal storage class. S3 Glacier Flexible Retrieval delivers the most flexible retrieval options that balance cost with access times ranging from minutes to hours and with free bulk retrievals. It is an ideal solution for backup, disaster recovery, offsite data storage needs, and for when some data occasionally need to be retrieved in minutes, and you don’t want to worry about costs. S3 Glacier Flexible Retrieval is designed for 99.999999999% (11 nines) of data durability and 99.99% availability by redundantly storing data across multiple physically separated AWS Availability Zones in a given year. For more information, visit the [**Amazon S3 Glacier storage classes page »**](https://aws.amazon.com/s3/storage-classes/glacier/)

**Key features:**

- Backup and archive data that is rarely accessed and low cost
- Designed to deliver 99.99% availability with an [availability SLA](https://aws.amazon.com/s3/sla/) of 99.9%
- Supports SSL for data in transit and encryption of data at rest
- Ideal for backup and disaster recovery use cases when large sets of data occasionally need to be retrieved in minutes, without concern for costs
- Configurable retrieval times, from minutes to hours, with free bulk retrievals
- S3 PUT API for direct uploads to S3 Glacier Flexible Retrieval, and S3 Lifecycle management for automatic migration of objects

### Amazon S3 Glacier Deep Archive

S3 Glacier Deep Archive is Amazon S3’s lowest-cost storage class and supports long-term retention and digital preservation for data that may be accessed once or twice in a year. It is designed for customers—particularly those in highly-regulated industries, such as financial services, healthcare, and public sectors—that retain data sets for 7—10 years or longer to meet regulatory compliance requirements. S3 Glacier Deep Archive can also be used for backup and disaster recovery use cases, and is a cost-effective and easy-to-manage alternative to magnetic tape systems, whether they are on-premises libraries or off-premises services. S3 Glacier Deep Archive complements Amazon S3 Glacier, which is ideal for archives where data is regularly retrieved and some of the data may be needed in minutes. All objects stored in S3 Glacier Deep Archive are replicated and stored across at least three geographically-dispersed Availability Zones, protected by 99.999999999% of durability, and can be restored within 12 hours. For more information, visit the [**Amazon S3 Glacier storage classes page »**](https://aws.amazon.com/s3/storage-classes/glacier/)

**Key features:**

- Archive data that is very rarely accessed and very low cost
- Designed to deliver 99.99% availability with an [availability SLA](https://aws.amazon.com/s3/sla/) of 99.9%
- Ideal alternative to magnetic tape libraries
- Retrieval time within 12 hours
- S3 PUT API for direct uploads to S3 Glacier Deep Archive, and S3 Lifecycle management for automatic migration of objects

## Data residency and isolation

### Amazon S3 storage classes for AWS Dedicated Local Zones

In AWS Dedicated Local Zones, the S3 Express One Zone and S3 One Zone-Infrequent access storage classes are purpose-built to store data in a specific data perimeter to support your data isolation and data residency use cases. Dedicated Local Zones are a type of AWS infrastructure that is fully managed by AWS, built for exclusive use by you or your community, and placed in a location or data center specified by you to help you comply with regulatory requirements. Both storage classes store data in a single Dedicated Local Zone and are supported in directory buckets. S3 supports the AWS Management Console, AWS SDKs, and S3 APIs, so you can run S3 based applications in Dedicated Local Zones. S3 Express One Zone is a high-performance storage class purpose-built to deliver consistent single-digit millisecond data access for your most frequently accessed data and latency-sensitive applications. Amazon S3 One Zone-Infrequent Access is designed for data that is accessed less frequently and is ideal for backups. 

Key features:

- Store S3 objects in a specific data perimeter
- Enforce security within a data perimeter using AWS Identity and Access Management (IAM)
- Audit bucket and object-level access for governance and compliance use cases with AWS CloudTrail
- Designed to durably and redundantly store data in a single Dedicated Local Zone

### Amazon S3 on Outposts

Amazon S3 on Outposts delivers object storage to your on-premises AWS Outposts environment. Using the S3 APIs and features available in AWS Regions today, S3 on Outposts makes it easy to store and retrieve data on your Outpost, as well as secure the data, control access, tag, and report on it. S3 on Outposts provides a single Amazon S3 storage class, named 'OUTPOSTS', which uses the S3 APIs, and is designed to durably and redundantly store data across multiple devices and servers on your Outposts. The S3 Outposts storage class is ideal for workloads with local data residency requirements, and to satisfy demanding performance needs by keeping data close to on-premises applications.

Key features:

- Store S3 objects in your on-premises AWS Outposts environment 
- S3 Object compatibility and bucket management through the S3 SDK
- Designed to durably and redundantly store data on your AWS Outposts rack
- Encryption using SSE-S3 and SSE-C
- Authentication and authorization using IAM and S3 Access Points