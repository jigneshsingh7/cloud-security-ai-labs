# Example 2 start and stop ec2 instance

## 🎯 Problem Statement

Imagine there are **100 EC2 instances** in AWS.

These instances belong to **different teams**.

Example:

| Team | EC2 Instances |
| --- | --- |
| Payments | Payment-EC2-1, Payment-EC2-2, Payment-EC2-3 |
| Coupons | Coupon-EC2-1, Coupon-EC2-2, Coupon-EC2-3 |

Each team has its own IAM users.

### Requirement

- ✅ Payments users should manage **only Payments EC2s**
- ✅ Coupons users should manage **only Coupons EC2s**
- ❌ They should NOT manage each other's EC2 instances.

---

# 💡 Solution

AWS uses:

- **Resource Tags**
- **Principal (IAM User) Tags**
- **IAM Policy Variables**
- **Condition Element**

---

# 🏷️ Step 1: Tag the IAM User

Example:

| IAM User | Tag Key | Tag Value |
| --- | --- | --- |
| Rahul | team | payments |

---

# 🏷️ Step 2: Tag the EC2 Instance

| EC2 Instance | Tag Key | Tag Value |
| --- | --- | --- |
| Payment-EC2 | team | payments |
| Coupon-EC2 | team | coupons |

---

# 🏷️ Step 3: IAM Policy

Policy checks:

> Is the EC2's **team tag** equal to the IAM User's **team tag**?
> 

If **YES** → Allow

If **NO** → Deny

![image.png](Example%202%20start%20and%20stop%20ec2%20instance/image.png)