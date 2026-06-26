# IAM Fundamentals

# IAM Policies

IAM policy defines the **permissions** that a specific entity has in aws 

### Types of IAM Policy

![image.png](IAM%20Fundamentals/image.png)

| Policy Type | Remember in 2-3 Words |  |
| --- | --- | --- |
| Identity-Based Policy | **User Permissions** | attached to users,group, roles. etc (most imp will study in detail) |
| Resource-Based Policy | **Resource Permissions** |   • attached to s3,kms keys, ec2 etc 
  • this policy would over-ride Identity based policy.
  • you canspecify who has access to the resource and what they can do
  • ex only the files with SSE i.e encryption can be uploaded to the bucket  |
| Permissions Boundary | **Permission Limit** |   • here even if you grant more permission to a entity it wont be able to exceed permission boundary
  • EX in permission boundary if you assign s3*,ec2*,cloudwatch* now even if you assign a user administrator access he would not be able to do anything except the above |
| SCP (Service Control Policy) | **Account Limit** |   • You can associate a single service control policy at 100 accounts and whatever permissions that you give as part of the SCPs, all 100 accounts will be able to follow that.
  • You create the SCP once in the AWS Organizations Management Account and attach it to the required OU or Account.
  • For example, in this specific policy, you have ec2:StopInstances, ec2:TerminateInstances. There is a condition of multi-factor authentication. So if someone does not have a MFA set, he'll not be able to stop and terminate the instances. |
| ACL (Access Control List) | **Network Access** | AWS recommends using **IAM Policies + Bucket Policies** instead of ACLs.ACLs are considered **legacy access control** and are rarely used in modern AWS environments. |
| Session Policy | **Temporary Limit** |  |

# Identity based IAM Policy

![image.png](IAM%20Fundamentals/image%201.png)

### Managed policies:

standalone identity-based policies that you can attach to multiple user groups and roles in your account. 
where would you find these policy:- IAM ➖ policy (these policy dont get deleted if you delete the entity its attached to it would simply get detached)

#### Advantage of managed policy:

1. Reusability:- one policy can be attached to multiple entity
2. versioning and rollback:- when you change the customer managed policy the changed policy doesn’t overwrite the existing policy, but create a new version and you always have a option to go back to the previous version as AWS stores upto 5 versions of customer managed policy.

#### AWS managed :

you can attach it to user groups and roles but you would not be able to edit this policy and change anything 

#### Customer managed:

you can create and manage in your aws account. you can edit these policies yourself and attach it to user group and roles 

### Inline policy

policies that you directly attach to a user , group or a role. here you dont have the function of multi attached where you can attach one policy to multiple entities
they maintain one-to-one relationship between policy document and the entity attached and would be deleted if the entity is deleted (entity can be user, group or role)
how can you add this inline policy 
IAM→ go to user/group/role → add permission → create inline policy
Note: there is no versioning in inline policy 
when to use the inline policy:- when there is exception ex there is a group with 20 people who have only ec2 access and you now want to give one user access to billing too so that he can view bills in this case you attach inline policy to the user 

# IAM policy structure

![image.png](IAM%20Fundamentals/image%202.png)

# Simple Formula

Principal = Who
Action = What they can do
Resource = On what resource
Effect = Allow or Deny
Condition (optional) = when

| Version | policy language version | always 2012-10-17 |
| --- | --- | --- |
| Id | policy identifier (optional) | just to name the policy  |
| Statement | one or more  | depends on how many things you wanna do in above ex we have one stmt  |
| Sid | statement id (optional) | which stmt it is in your policy 1, 2 … |
| Effect | allow or deny |  |
| Principal | here you specify who gets the permissions
OR
to which user/account/role this policy would be allowed  |  example :- Specific IAM User "AWS": "arn:aws:iam::123456789012:user/Jignesh”
Entire AWS Account  "AWS": "123456789012”
Everyone (Public Access)  "Principal": "*” |
| Action | What can they do? | "s3:GetObject", "s3:PutObject” |
| Resource | on which resource this policy applies to | specific resource like that bucket or user 
or apply to all resource *  |
| Condition | when will this policy take effect (optional). | ex if nothing mentioned then always or else for specific condition like user is xyz or bucket is abc. |

> ARN: amazon resource name
> 
> 
> format is :- 
> arn:partition:service:region:account-id:resource-type:resource-id
> 
> example:-
> 
> arn:aws:ec2:us-east-1:12345678:instance-id
> arn:aws:IAM::123456789:user:jignesh
> 

## NotAction with Allow

![image.png](IAM%20Fundamentals/image%203.png)

- here in the above policy example we have allowed all the actions except IAM 
note that we dont deny anything or even IAM but we have specifically not allowed IAM.
- In second example we have allowed all action on  S3 bucket except of delete bucket

## NotAction with Deny (very confusing so read carefully )

![image.png](IAM%20Fundamentals/image%204.png)

- this is the policy similar to what we use at Clear-trail where we deny everything to user except IAM if MFA is not present 
why MFA not present condition there:-  coz you would need IAM first to set MFA too
- here we have denied all action on all resources except (that is not) IAM,
condition to if multi-factor authentication is not present
- Note:- but this not at all means that the IAM is allowed for all the users with MFA.
we need to specifically all that too in a different policy or in the next stmt

## NotAction  to restrict to one Region (very confusing so read carefully )

![image.png](IAM%20Fundamentals/image%205.png)

- **Policy 1: Deny Everything Outside eu-central-1 except the global services**
    - What does it do?
    
    **1. Users can perform all AWS actions only in the eu-central-1 region.**
    
    If they try to launch EC2, create RDS, create Lambda, etc. in us-east-1 or ap-south-1 → **Denied**.
    
    **2. CloudFront, IAM, Route53, and Support are exempt from this restriction.**
    
    These services can still be used from any region because they are global services.
    
    Examples:
    
    - Create IAM User → Allowed
    - Create Route53 Record → Allowed
    - Create CloudFront Distribution → Allowed
    - Launch EC2 in us-east-1 → Denied
- **Policy 2: Deny Everything Outside eu-central-1 Except S3**
    - What does it do? (2 Points)
    
     **1. All AWS services except S3 are restricted to eu-central-1.**
    
    Examples:
    
    - EC2 in us-east-1 → Denied
    - Lambda in us-east-1 → Denied
    - RDS in us-east-1 → Denied
    
    **2. S3 operations are allowed from any region.**
    
    Examples:
    
    - Create S3 Bucket → Allowed
    - Upload Object → Allowed
    - Download Object → Allowed
    
    Even if the request comes from outside eu-central-1.
    

# everything compiled

![image.png](IAM%20Fundamentals/image%206.png)

# Types of Principal to whom you can assign iam policies

![image.png](IAM%20Fundamentals/image%207.png)

![image.png](IAM%20Fundamentals/image%208.png)

# IAM security Tools;

1. IAM credentials Report: {Account level} 

it would list all your accounts users and the status of their various credentials.
go to iam console and you would find it 

1. IAM access advisor: {User Level}

it shows the permissions granted to the users and when those services were last used.
we can use this to review and revise the policy assigned to user
go to iam console and then go to user and scroll

1. IAM Access Analyzer: {External}

![image.png](IAM%20Fundamentals/image%209.png)

that is used to find out which resources are going to be shared externally. So this applies with S3 buckets, IAM roles, KMS keys, Lambda functions and layers, SQS queues, and Secrets Manager Secrets.

So the idea is that some of these, obviously, can have resource policies attached to them, or they can be shared with other accounts. But sometimes you forget about sharing these items and it can be a security risk for your company because some of the data may be accessible by external sources. And so, you define a zone of trust, which is going to correspond to your AWS accounts or your entire AWS organization. 

Then anything outside your zone of trust that has access to the resources said above are going to be reported as findings So for example, we have an S3 bucket, we can share it with a specific role, a user, an account, an external client by IP, or a VPC endpoint. But if we define the zone of trust to be our accounts and only the role, the user, and the VPC endpoints are within our accounts, then the accounts and the external clients are going to be flagged as a finding, and you can look at it within the console to take action if you think this is a security risk.

![Iam access analyzer extra things it does](IAM%20Fundamentals/image%2010.png)

Iam access analyzer extra things it does
