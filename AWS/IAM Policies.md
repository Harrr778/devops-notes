### Difference between inline policy and managed policy

|Feature|Managed Policy|Inline Policy|
|---|---|---|
|**Definition**|Pre-defined policies created and managed by AWS|Custom policies created and managed by the user|
|**Scope**|Can be attached to multiple users, groups, or roles|Attached to a single user, group, or role|
|**Management**|Managed by AWS, updates are automatically applied|Managed by the user, requires manual updates|
|**Reusability**|Highly reusable across multiple identities|Less reusable, specific to a single identity|
|**Best Practice**|Use for common permissions and centralized management|Use for specific, unique permissions that need to be isolated to a single identity|

### IAM Policy Types 
Based on the provided search results, IAM (Identity and Access Management) in AWS offers four types of policies:

1. **Identity-Based Policies**: Attached to an identity (user, group, or role), these policies define the permissions for that specific identity. They are used to control access to AWS resources and services.
2. **Resource-Based Policies**: Attached to a specific resource (e.g., S3 bucket, EC2 instance), these policies define the permissions for that resource. They specify which identities have access to the resource and under what conditions.
3. **Service Control Policies (SCPs)**: These policies control the actions that can be performed by IAM users and roles across AWS services. They are used to enforce organizational compliance and governance.
4. **Permissions Boundary Policies**: These policies define the maximum possible permissions that an IAM role can have. They are used to restrict the permissions granted to roles created by CI/CD pipelines or other automated processes.

Here's a summary of the policies and their uses:

| Policy Type | Attached To | Purpose |
| --- | --- | --- |
| Identity-Based | Identity (user, group, role) | Define permissions for a specific identity |
| Resource-Based | Resource (e.g., S3 bucket, EC2 instance) | Define permissions for a specific resource |
| Service Control Policies (SCPs) | N/A | Enforce organizational compliance and governance across AWS services |
| Permissions Boundary Policies | IAM role | Restrict permissions granted to roles created by automated processes |

Note that Managed Policies and Customer Managed Policies are not separate policy types, but rather categories of policies. Managed Policies are created and managed by AWS, while Customer Managed Policies are created and managed by users in their AWS accounts. Inline Policies are embedded within an identity or resource, but are not a distinct policy type.

For more information, refer to the AWS documentation and the provided search results.

# Types of IAM Users

Based on the provided search results, AWS Identity and Access Management (IAM) supports the following types of users:

1. **IAM User**: An IAM user is an entity you create in AWS. This user is an identity within your AWS account that’s granted specific custom permissions. IAM users have a name and password used to sign in to the AWS Management Console.
2. **Root User**: The root user is the initial sign-in identity for an AWS account. It has complete access to all AWS services and resources in the account. However, AWS strongly recommends not using the root user for everyday tasks and instead creating IAM users with limited permissions.
3. **IAM Identity Center User**: IAM Identity Center users are members of AWS Organizations and can be ==**granted access to multiple AWS accounts**== and applications through the AWS access portal. They can use their corporate credentials to sign in if their company has integrated Active Directory or another identity provider with IAM Identity Center.
4. **Federated Identity**: With web identity federation, you can receive an authentication token and exchange it for temporary security credentials in AWS that map to an IAM role with permissions to use the resources in your AWS account. Federated identities sign in using an external identity provider.
5. **AWS Builder ID User**: AWS Builder ID users are a type of user that represents an individual and ==**allows access to AWS services and tools without an AWS account**==. They sign in to specific AWS services or tools using their AWS Builder ID profile.

Note that these types of users are not mutually exclusive, and you may use a combination of them in your AWS environment. For example, you might create IAM users for your workforce and use federated identities for external partners or customers.