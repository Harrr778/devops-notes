---
Title: Azure Notes
date: 2025-04-15
tags:
  - Azure
---

Azure is **Microsoft's cloud platform**. It helps you run websites, store data, use databases, build apps, and more.

It offers:-

> **IaaS** (you manage apps, Azure manages hardware)
> **PaaS** (Azure handles most of the setup for you)
> It works well with **Microsoft tools** and supports many **programming languages.** Azure runs in over **60 regions** worldwide, so it's fast and reliable almost anywhere.

---

## Azure vs AWS Resources(services) Comparison:-

1> **Compute Azure**: Virtual Machines, VM Scale Sets, Azure Functions. AWS: EC2, Auto Scaling, Lambda.

2> **Storage Azure**: Blob Storage, File Storage, Disk Storage, Archive Storage AWS: S3, EFS, EBS, Glacier

3> **Database Azure**: Azure SQL, Cosmos DB, MySQL, PostgreSQL AWS: RDS, DynamoDB, Aurora, Redshift

4> **Networking Azure**: Virtual Network, Load Balancer, Application Gateway. AWS: VPC, ELB, API Gateway.

5> **Identity Azure**: Azure Active Directory(intra ID) AWS: IAM

---

## Azure Resource Manager :-

It is the deployment and management system for Azure. It lets you organize, deploy, and manage all your cloud resources (like VMs, storage, databases, etc.) in a consistent way.

**Resource Group**: A container to group related resources.

**ARM Template**: A JSON file used to automate and repeat deployments (like Infrastructure as code).

**Declarative**: You define what you want, and ARM handles how to create it.

---

## TENANT:-

> An Azure tenant is essentially your **organization's secure identity provider** and represents your organization within Microsoft's cloud ecosystem.

> A tenant is like your **organization's secure container** in Azure where all users, groups, and permissions are stored and managed.

> A tenant is **tied to a specific domain**, like https://www.google.com/search?q=cloudblitz.in.onmicrosoft.com.

It holds:
- Users and groups
- Applications and service principals
- Access and identity settings
- One tenant can manage Multiple Azure subscriptions.**(without tenant we can't create subscription)**
- It's the **top-level boundary** for identity and access control.

---

## Subscription:-

> In Azure, a subscription is like a container for your resources and a billing unit.

> > A subscription in Azure is where you create, manage, and pay for your cloud resources (like VMs, databases, storage, etc.).

> It tracks usage and costs for billing purposes.

> > You can have multiple subscriptions under a single Azure account - useful for separating:

- Teams -Projects -Environments (dev, test, prod)

> Subscriptions are linked to an Azure Active Directory (Azure AD) tenant for identity and access management.

just like :- Azure Account → contains → Subscriptions → contain → Resource Groups → contain → Resources.


---

## RESOURCE GROUP:-

> > A Resource Group is like a folder or logical container that groups Azure resources (like VMs, databases, storage) that belong together.

- You create, manage, and delete resources together.
- Helps with organization, access control, and billing.
- You can apply tags, policies, and permissions at the resource group level.
- Deleting a resource group deletes all resources inside it.
- We can move resources from one r.g to another r.group.(creat new R.G) centarl-us to east-us

---

## Active Directory

> > Azure Active Directory (Azure AD) is Microsoft's cloud-based identity and access management (IAM) service. Azure AD helps you sign in and access Microsoft services like Azure, Microsoft 365, and custom apps - securely.

- Single Sign-On (SSO): Sign in once and access multiple apps.
- Multi-Factor Authentication (MFA): Extra security with phone or app verification.
- Access Control: Manage who can access what.
- Directory Services: Like storing and managing users, groups, and devices.

---

### Types of Users in Azure:-

1> Microsoft Account Users

- Personal accounts like [email address removed].

2> Work Account Users:-

- Created through Azure Active Directory (Azure AD).
- Used for employees or team members of an organization.

3> Guest Users (B2B Collaboration)

- External users invited to your tenant.
- Can be assigned limited permissions.

---

### roles in Azure:-

1. Azure RBAC Roles (Manage resources):- 

a> Used to manage Azure resources like VMs, storage, etc.
b> Owner - Full access to resources including delegation. 
c> Contributor - Can create/manage resources but cannot grant access. 
d> Reader - Can view resources but cannot make changes. 
e> Custom roles - customize permissions for specific needs.

---

### Azure Contributor is like a manager who can:

- Create new resources (like virtual machines, databases, websites)
- Change existing resources (update settings, modify configurations)
- Delete resources they don't need anymore

***But they have one key limitation:

They cannot give other people permission to access these resources.

---

### 2. Azure AD Roles (Manage Identities) Used to manage users, groups, directory settings.

| Role Name<br>               | Purpose                                            |
| --------------------------- | -------------------------------------------------- |
| - Global Administrator      | Full control over Azure AD and Microsoft services. |
| - User Administrator        | Can create and manage users and groups.            |
| - Billing Administrator     | Manages subscriptions and billing.                 |
| - Application Administrator | Manages app registrations and permissions.         |

### **Types of Azure Policies:-** 
1. **Built-in Policie**s:- Predefined by Microsoft. 
Examples: - 
- Only allow specific VM sizes. 
- Require tags on all resources. 
- Deny unapproved regions. 

1. **Custom Policies:-** 
- Created by you or your organization. 
- Useful when built-in policies don't meet your exact needs. 
- Written in JSON format.

## Storage Account In Azure 

A Storage Account gives you access to Azure Storage services, which include:- 
* Blob Storage - for unstructured data (like images, videos, backups). 
* File Storage - managed file shares (like SMB/NFS protocol). 
* Queue Storage - for message queuing. 
* Table Storage - for NoSQL key-value data. 

main points:- 
- Unified storage solution for various data types (blobs, files, queues, tables). 
- Highly available and durable with redundancy options. 
- Secure access through multiple authentication methods. 
- Scalable to handle growing storage needs. 
- ---------------------------------------- 
### Storage Account Types 
* **Standard general-purpose v2**: 
- Cost-effective option for most scenarios 

* **Premium performance**: 
- For high-throughput applications 

* **BlockBlobStorage:** 
- Optimized for block blob operations

* **FileStorage**: - 
* Optimized for file share operations 

* **Storage v1 (legacy)**: - 
* Older generation (not recommended for new applications) 

| Type                          | Description                                                                  |
| ----------------------------- | ---------------------------------------------------------------------------- |
| **General Purpose v2 (GPv2)** | Most commonly used. Supports all types: blobs, files, queues, tables, disks. |
| **General Purpose v1 (GPv1)** | Older version. Cheaper but fewer features. Generally not recommended now.    |
| **Blob Storage**              | Optimized for storing unstructured object data (like media, logs, backups).  |
| **File Storage**              | Used for cloud-based file shares (via SMB protocol).                         |
| **BlockBlobStorage**          | Premium storage for high-performance workloads.                              |
| **Premium File Storage**      | For I/O-intensive enterprise file workloads.                                 |

Azure Blob Storage offers three different blob types, each designed for specific purposes: 
### 1. Block Blobs:- 
- Structure: Composed of individually managed blocks of data (up to 100 MB each) 
- Maximum size: Up to 190.7 TB

Use cases:
- Text and binary files (documents, images, videos)
- Media storage and streaming
- Backup and restore operations
- Distributed access applications
- Web content storage

### 2. Page Blobs:-

- Structure: Collection of 512-byte pages optimized for random read/write operations
- Maximum size: Up to 8 TB

Use cases:
- Virtual machine disks (VHD files)
- Database files requiring random access
- Applications that need frequent read/write operations
- Scenarios requiring random access to parts of the file

### 3. Append Blobs:-

- Structure: Optimized for append operations, built from blocks like block blobs
- Maximum size: Up to 195 GB

Use cases:
> Logging (application logs, device telemetry)
> Audit trails
> Event data collection
> Any scenario where data is continuously added but rarely modified

----------------------------------------

### **Access Tiers (For Blob Storage type):-**

| Tier    | Use Case                        |
| ------- | ------------------------------- |
| Hot     | Frequent access data            |
| Cool    | Infrequently accessed data      |
| Archive | Rarely accessed, long-term data |
| cold    |                                 |

### Common Use Cases

1. Storing application data
2. Hosting websites and web applications
3. Backup and disaster recovery
4. Big data analytics
5. Content distribution
