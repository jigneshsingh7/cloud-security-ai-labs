# EXAMPLE

# M1.1 Notes – How a Solutions Architect Works in a Real Consulting Engagement

## Example Project

**Client:** Apex Manufacturing Ltd.

**Business Goal:** Build a cloud-based HR Management System.

---

# The Most Important Principle

> **Customers don't ask for AWS services.**
> 
> 
> **Customers ask for business outcomes.**
> 
> The architect's job is to convert business outcomes into technical capabilities and then into technology.
> 

---

# Real Consulting Workflow

## Phase 1 – Business Discovery Meeting

### Participants

- CEO
- HR Director
- Solutions Architect

### Purpose

Understand the business problem.

### What is NOT discussed?

- EC2

- AWS

- RDS

- Cloud
- Architecture

### Questions Asked

#### Business Goals

- Why are we building this application?
- What problem are we trying to solve?
- What does success look like?

#### Users

- Who will use the application?
- Employees?
- HR Team?
- Managers?

#### Growth

- Current users?
- Expected users after five years?

#### Budget

- Budget limitations?
- Timeline?

### Output

Business Requirements Document

---

## Phase 2 – Functional Discovery

### Participants

- HR Director
- Solutions Architect

### Purpose

Understand what the application should do.

### Questions

What features are required?

Examples:

- Employee Records
- Leave Management
- Attendance
- Performance Reviews
- Employee Onboarding
- Document Upload

### Output

Functional Requirements

---

## Phase 3 – Technical Discovery

### Participants

- CTO
- Solutions Architect

### Purpose

Understand the existing technical environment.

### Questions

Current Infrastructure

- Existing HR System?
- Existing Database?
- Active Directory?
- Microsoft Entra ID?
- Email System?

Integrations

- Payroll System?
- Third-party APIs?
- Existing Applications?

Availability

- Required Uptime?
- Disaster Recovery?
- Compliance?

### Output

Technical Requirements

---

## Phase 4 – Internal Architecture Workshop

### Participants

- Solutions Architect
- CTO

### Purpose

Convert Business Requirements into Technical Requirements.

---

### Business Requirements

- HR digitization
- Employee Self-Service
- Remote access
- Secure employee records
- Integration with Payroll
- Support company growth
- 99.9% availability

---

### Technical Requirements

- Authentication
- Authorization
- Secure API Integration
- Object Storage
- Relational Database
- Monitoring
- Logging
- Encryption
- Backup
- High Availability
- Scalability

**Important**

At this stage there should still be **no AWS services**.

---

## Phase 5 – Architecture Workshop

### Participants

- Solutions Architect
- Cloud Engineers

### Purpose

Design the logical solution.

Discussion includes:

- Authentication
- Business Logic
- Database
- APIs
- Storage
- Monitoring
- Security

Cloud Engineers may suggest technologies, but the architect evaluates trade-offs before selecting them.

---

## Phase 6 – Technology Selection

Only after requirements and logical architecture are finalized do we select AWS services.

Example Mapping

| Technical Capability | AWS Service (Example) |
| --- | --- |
| DNS | Route 53 |
| Global Content Delivery | CloudFront |
| Web Protection | AWS WAF |
| Load Balancing | Application Load Balancer |
| Compute | EC2 Auto Scaling Group |
| Database | Amazon Aurora PostgreSQL |
| Object Storage | Amazon S3 |
| Authentication | Microsoft Entra ID Federation |
| Secrets | AWS Secrets Manager |
| Encryption | AWS KMS |
| Monitoring | Amazon CloudWatch |
| Audit | AWS CloudTrail |

---

## Phase 7 – CEO Presentation

### Audience

CEO

### Diagram Used

Business Diagram

### Discussion

Focus on business outcomes.

Example:

- Faster HR operations
- Secure employee information
- Supports future growth
- Remote access
- Payroll integration
- High availability

No AWS terminology should be used.

---

## Phase 8 – CTO Presentation

### Audience

CTO

### Diagram Used

Logical Architecture

Example Components

- Users
- Authentication
- HR Application
- Business Services
- Employee Database
- Document Storage
- Payroll Integration

Focus on technical capabilities rather than AWS products.

---

## Phase 9 – Engineering Handover

### Audience

Cloud Engineers

### Diagram Used

AWS Physical Architecture

Example

Users

↓

Route 53

↓

CloudFront

↓

AWS WAF

↓

Application Load Balancer

↓

Auto Scaling Group

↓

EC2

↓

Aurora PostgreSQL

↓

Amazon S3

↓

CloudWatch

↓

CloudTrail

Engineers receive implementation details.

---

# Diagram Types Used in Real Projects

## 1. Business Diagram

Audience

- CEO
- Business Stakeholders

Purpose

Explain business workflow.

Uses business terms only.

Example Labels

- Employees
- HR Team
- Managers
- Payroll System
- HR Management System

---

## 2. Logical Architecture Diagram

Audience

- CTO
- Solutions Architects

Purpose

Explain technical capabilities.

Uses capability names.

Example Labels

- Authentication
- Business Logic
- API Integration
- Employee Database
- Document Storage
- Notification Service
- Audit Logging

No AWS services.

---

## 3. Physical (AWS) Architecture Diagram

Audience

- Cloud Engineers
- DevOps Team
- Operations Team

Purpose

Explain implementation.

Uses AWS services.

Example Labels

- Route 53
- CloudFront
- AWS WAF
- Application Load Balancer
- EC2
- Aurora
- Amazon S3
- CloudWatch
- CloudTrail

---

# Golden Rule

Business Problem

↓

Business Requirements

↓

Technical Requirements

↓

Logical Architecture

↓

Technology Selection

↓

AWS Services

↓

Implementation

Never skip directly from the Business Problem to AWS Services.

---

# Audience vs Communication

| Audience | Diagram | Language |
| --- | --- | --- |
| CEO | Business Diagram | Business outcomes, cost, growth, risk |
| HR Director | Business Diagram | HR workflow, approvals, onboarding |
| CTO | Logical Architecture | Authentication, APIs, scalability, security |
| Solutions Architect | Logical + ADR | Trade-offs, patterns, constraints |
| Cloud Engineers | AWS Physical Architecture | ALB, EC2, VPC, Aurora, WAF |
| Security Team | Security Architecture | IAM, KMS, Logging, Encryption |
| Finance Team | Cost View | Budget, TCO, Operational Cost |

---

# Key Learning from M1.1

A Solutions Architect does not begin with AWS services.

A Solutions Architect begins with understanding the business, translates it into technical capabilities, validates those capabilities with stakeholders, and only then chooses the most appropriate technologies.

This is the mindset that differentiates an experienced Cloud Engineer from a Solutions Architect.