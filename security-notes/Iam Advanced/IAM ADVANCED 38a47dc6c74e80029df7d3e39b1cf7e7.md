# IAM ADVANCED

## Iam Policy Evaluation

why it is important?

it happens sometime that a user is not able to perform certain actions even though we have given him the permission in such scenarios Policy evaluation logic plays an important role to help you identify where the problem lies and also the rectifying solutions.

AWS has too many types of policies like Identity based, resource based policies, SCP, ACL, Inline policies and permission boundaries and session policies. so there is a chance that there could exist a contradictory policies too so in such scenarios what will be the final decision?
will the user be allowed or will he be denied 

`Note: in AWS by default all the requests are implicitly denied with the exception of Root user who has the full access` 

for example if you create a new user in AWS he would have no permission to perform any actions by default and this is called as **Default Deny**

- **Explicit Allow** in an **Identity or resource based policy** can override this default deny ex: allow jay for s3* only then user jay will have access to s3
- Any Explicit Deny = Final Deny

```json
# we created this as an inline policy for user jay
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "S3FulLAccess",
            "Effect": "Allow",
            "Action": "s3:*",
            "Resource": "*"
        }
    ]
}

```

```json
# we created this resource-based policy for user jay
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Principal": {
                "AWS": "arn:aws:iam::042025557788:user/jay"
            },
            "Action": "s3:GetObject",
	            "Resource": "arn:aws:s3:::demo-user-sample-bucket/*"
        },
        {
            "Effect": "Allow",
            "Principal": {
                "AWS": "arn:aws:iam::042025557788:user/kplabs-video-user"
            },
            "Action": "s3:ListBucket",
            "Resource": "arn:aws:s3:::demo-user-sample-bucket"
        }
    ]
}
```

 

![image.png](IAM%20ADVANCED/image.png)

when the case is of Identity based policy and resource based policy its combination of both i.e.
you can give some permission at each level and combination of permissions would work 
ex: user jay has been given DescribeS3bucket at user(identity level) and allow puts3object at resource level so now jay will have both permissions 

![image.png](IAM%20ADVANCED/image%201.png)

when its between identity based policy and permission boundary(user or role level and not group) and Organization SCP only the common policies win no matter what acces you give at identity level if its out of the permission boundary it wont be allowed
Ex: permission boundary says Ec2 full access and at user level you give user jay permission for Ec2start and Ec2stop instance and s3 full access.
now user jay would not be able to do any thing with s3 because its out of permission and also on ec2 he would just have start and stop permissions.

![image.png](IAM%20ADVANCED/image%202.png)

![image.png](IAM%20ADVANCED/image%203.png)

# Condition Element in IAM Policy

whenever we are writing complex set of IAM policies, condition element is one of the common element that you will be using to fine tune our policies for our use case.

condition element, also referred to as a condition block. It allows you to specify a condition whenever you are writing IAM policy.

#### condition element format

```json
"Condition":{"{condition-operator}":{"{condition-key}":"{condition-value}"}}
example
"Condition":{"IpAddress":{"aws:SourceIp":"100.99.88.77/32"}}

this condition would restrict the user to do action only when he is via this ip example from office network 
```

![image.png](IAM%20ADVANCED/image%204.png)

![image.png](IAM%20ADVANCED/image%205.png)

![image.png](IAM%20ADVANCED/image%206.png)

> use this document as reference whenever you need more information on condition operators.
[IAM JSON policy elements: Condition operators - AWS Identity and Access Management](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements_condition_operators.html)
> 

> whenever you are creating a policy under user inline policy or permission GUI also gives us option to add condition from there itself named “**request conditions-optional**”
> 

### IAM Policy Variable

So let's say that you're working as a DevOps engineer and your organization has a requirement where you want to create a IAM policy to allow the IAM users to create their own set of access secret keys.

So this is a very simple requirement where every IAM user should be allowed to create their own set of access secret keys.

![image.png](IAM%20ADVANCED/image%207.png)

Now, although this is a working policy, but it is not optimized for larger environments, we would have to create separate policy for every user, and this is not scalable and is alot of manual work changing username in each policy

So in order to overcome this, we can make use of the policy variables.

Now in this kind of an approach, you see, instead of specifying the username like Alice, Bob, etc, we have replaced it with a policy variable with AWS colon username.

So what this will do is that when this policy gets associated with a entity of Alice, then automatically the AWS colon username will be computed with the Alice when the request is made. Similarly, you can associate the same policy with hundred of users. It does not really matter. This specific variable will automatically be computed for you and this can make life simple.

![policy variable](IAM%20ADVANCED/image%208.png)

policy variable

#### policy variables format

Now the variable is marked with a dollar prefix followed by the pair of curly braces and inside the curly brace characters you can include the name of the value from the request that you want in the policy.

![image.png](IAM%20ADVANCED/image%209.png)

example: ${aws:username}

[Example 2 start and stop ec2 instance ](IAM%20ADVANCED/Example%202%20start%20and%20stop%20ec2%20instance%2039847dc6c74e807d9aeefe5ef1cccd0e.md)

> 
> 
> 
> [IAM policy elements: Variables and tags - AWS Identity and Access Management](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_variables.html)
> aws documentation
> 

# ABAC & RBAC (Attribute based  access control vs role based)

RBAC: stands for the role-based access control and in this type of approach, the restriction of access is based on person's role within the organization.

RBAC vs ABAC

| RBAC | ABAC |
| --- | --- |
| Access based on Roles | Access based on Tags (Attributes) |
| Example: Developer Role | Example: Team=Red |
| Multiple policies | Fewer policies |
| Policies need updates when resources grow | Usually no policy updates; just tag new resources |
| Best for small organizations | Best for large and fast-growing organizations |

What is ABAC?

**ABAC (Attribute-Based Access Control)** is an authorization model where **permissions are granted based on attributes (tags)** instead of assigning permissions based on roles.

👉 In AWS, **Attributes = Tags (Key-Value pairs).**

Instead of asking:

> **"What role does this user have?"**
> 

ABAC asks:

> **"Do the user's tags match the resource's tags?"**
> 

If they match ✅ → Access Allowed If they don't ❌ → Access Denied

What are Attributes?

An **Attribute** is simply a **Key-Value Pair**. In AWS these are called **Tags**.

**Core Idea of ABAC**: AWS compares: **User Tags with Resource Tags** If they match, Access is granted.

When should you use ABAC?

Large Organizations, Hundreds or thousands of AWS Resources, Multiple Teams Frequently created EC2, S3, RDS, Lambda resources Dynamic environments where resources are created often

# AWS IAM Policy Logic

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "ec2:DescribeInstances"
            ],
            "Resource": "*"
        },
        {
            "Effect": "Allow",
            "Action": [
                "ec2:StartInstances",
                "ec2:StopInstances"
            ],
            "Resource": "*",
            "Condition": {
                "StringEquals": {
                    "ec2:ResourceTag/Team": "${aws:PrincipalTag/Team}"
                }
            }
        }
    ]
}

```

A simplified version:

```
Allow

StartInstances

StopInstances

ONLY IF

aws:PrincipalTag/Team

=

aws:ResourceTag/Team
```