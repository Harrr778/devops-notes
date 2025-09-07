### Google Cloud Platform (GCP)
Is Google's cloud computing service that offers a suite of computing services for building, deploying, and scaling applications.

**GCP provides:**

- Infrastructure (servers, storage, networks) that businesses can rent instead of building their own.

- Various computing services like data analytics, machine learning, and database management.

- Tools for developers to build and deploy applications quickly.

- Global network infrastructure for reliable, fast performance.

- Pay-as-you-go pricing model to reduce upfront investment.


-----------------------------------------------------------
### GCP Services Compared to AWS

1) Compute Services:-

GCP: Compute Engine (similar to AWS EC2) - Virtual machines in Google's data centers
AWS: Amazon EC2 - Elastic compute cloud for scalable virtual servers

2) Serverless Computing:-

GCP: Cloud Functions (similar to AWS Lambda) - Event-driven serverless functions
AWS: Lambda - Run code without provisioning servers

3) Container Services:-

GCP: Google Kubernetes Engine (GKE) - Managed Kubernetes service
AWS: Amazon EKS/ECS - Kubernetes and container orchestration services

4) Storage Solutions:-

GCP: Cloud Storage (similar to AWS S3) - Object storage for files
AWS: S3 (Simple Storage Service) - Object storage with industry-leading scalability

5) Database Services:-

GCP: Cloud SQL, Firestore, Bigtable (similar to AWS RDS, DynamoDB)
AWS: RDS, DynamoDB, Aurora - Relational and NoSQL database options

6) Big Data & Analytics:-

GCP: BigQuery (similar to AWS Redshift) - Serverless data warehouse
AWS: Redshift - Data warehouse for analytics


7) Networking :-

GCP: Cloud VPN, Cloud Load Balancing (similar to AWS VPN, ELB)
AWS: VPC, Route 53, Elastic Load Balancing - Networking Infrastructure

8) Identity Management :-

GCP: Cloud Identity (similar to AWS IAM) - Identity and access management
AWS: IAM (Identity Access Management) - User access and encryption keys

9) Monitoring & Management :-

GCP: Cloud Monitoring (similar to AWS CloudWatch) - Infrastructure monitoring
AWS: CloudWatch - Observability of resources and applications



Google Cloud Platform IAM Service:-

Google Cloud IAM (Identity and Access Management) Is GCP's permission management system that controls who can do what on which resources.

 **Key Components:**

- Principals: who can access resources (users, groups, service accounts)
- Roles: Collections of permissions (predefined, custom, or basic)
- Policies: Bindings between principals and roles on specific resources

**Main Features:**

- Hierarchical resource organization (organization -> folders -> projects -> resources).

- Least privilege principle through granular permissions.

- Centralized visibility and control across GCP resources.

- Conditions for temporary or attribute-based access.

- Audit logging to track who did what.

IAM is essential for securing your GCP environment by ensuring the right people have appropriate access to necessary resources while preventing unauthorized access to sensitive systems and data.



### GCP IAM Roles and Policies

**Types of Roles :-**

1. Basic (Primitive) Roles

- Owner: Full access to all resources
- Editor: Modify access to resources
- Viewer: Read-only access
- Billing Administrator: Manage billing but not resources

2. Predefined Roles

- Service-specific roles: Tailored permissions for specific GCP services
- Examples: Compute Admin, Storage Admin, BigQuery User
- Designed for common use cases and job functions

3. Custom Roles

- User-defined sets of permissions
- Created at organization or project level
- Useful when predefined roles don't meet your needs
- Can be modified as requirements change
************************************************************

**Types of Policies**

1. IAM Policy


- Defines who (principal) has what access (role) to which resource
- Represented as a collection of bindings
- Attached to resources at various levels in the resource hierarchy

2. Organization Policy

- Centralized control over organization's resources
- Configures constraints on resource behavior
- Examples: restrict resource locations, limit service account usage

3. Role Binding Policy

- Associates principals with roles
- Can include conditions for more granular control

4. Conditional Role Bindings

- Time-limited access (temporary access)
- Access based on resource attributes
- Access based on request attributes (like IP address)

5. Allow Policies vs Deny Policies

- Allow policies grant permissions
- Deny policies explicitly block access (override allow policies)


##### IAM follows an "inheritance" model where policies applied at higher levels (organization, folder) flow down to contained resources unless explicitly overridden.
-------------------------------------------------------------


