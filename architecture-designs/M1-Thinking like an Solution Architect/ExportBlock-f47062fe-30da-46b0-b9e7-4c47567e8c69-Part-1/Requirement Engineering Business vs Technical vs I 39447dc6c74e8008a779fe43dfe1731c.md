# Requirement Engineering Business vs Technical vs Implementation

[Cheat Sheet](Requirement%20Engineering%20Business%20vs%20Technical%20vs%20I/Cheat%20Sheet%2039447dc6c74e80cdb0d6ced6f80be4ef.md)

**A.R.C.H.I.T.E.C.T. Framework**:

| Letter | Meaning | Core Question |
| --- | --- | --- |
| **A** | **Actors** | Who are the users and stakeholders? |
| **R** | **Requirements** | What are the business and functional requirements? |
| **C** | **Constraints** | Budget, timeline, compliance, legacy systems? |
| **H** | **High Availability** | Uptime, DR, RTO/RPO, scalability? |
| **I** | **Integrations** | What existing systems, APIs, and identity providers are involved? |
| **T** | **Threats** | Security, compliance, privacy, operational risks? |
| **E** | **Evolution** | Growth, future expansion, expected scale? |
| **C** | **Cost** | Budget, FinOps, optimization priorities? |
| **T** | **Technology** | Only now: which architecture and AWS services satisfy the requirements? |

# Engineer vs Solutions Architect Mindset

| Cloud Engineer | Solutions Architect |
| --- | --- |
| Focuses on implementation | Focuses on solving business problems |
| Starts with AWS services | Starts with business requirements |
| Builds infrastructure | Designs systems |
| Thinks "How do I build it?" | Thinks "Why are we building it?" |
| Optimizes resources | Optimizes business outcomes |

# The Architect's Thought Process

```
Business Problem
        ↓
Business Requirements
        ↓
Technical Requirements
        ↓
Architecture
        ↓
AWS Services
        ↓
Implementation
```

> **Golden Rule: Never skip directly from the business problem to AWS services.**
> 

# The First Rule of Architecture

> **Customers don't buy AWS services.**
> 
> 
> **Customers buy business outcomes.**
> 

The architect's job is to translate those outcomes into technical capabilities and then select the right technologies.

# Discovery Before Design

A Solutions Architect begins with questions—not answers.

Key discovery areas:

| Category | Example Questions |
| --- | --- |
| Business Goals | Why is the application being built? What problem does it solve? |
| Users | Who will use it? Employees, HR, managers, contractors? |
| Functional Requirements | What features are required? |
| Scale | Current users? Future growth? Peak traffic? |
| Geography | Where are users located? Any data residency needs? |
| Availability | Required uptime? Critical business periods? |
| Security | What data is sensitive? Any compliance requirements? |
| Integrations | Existing systems? Identity provider? Payroll? |
| Budget | Cost constraints? Operational team size? |

---

# Architecture Decision Flow

```
Understand
        ↓
Clarify
        ↓
Prioritize
        ↓
Design
        ↓
Evaluate Trade-offs
        ↓
Defend the Decision
```

# Requirement Hierarchy

## Business Requirements

These describe **what the client wants to achieve**. what does the business do ?

Examples:

- HR Management System
- Internet-accessible application
- Support 5,000 employees
- Scale to 12,000 employees
- 99.9% availability
- Secure employee information
- Integration with payroll system
- Corporate login
- Multi-country access

---

## Technical Requirements

These describe **the technical capabilities needed** to meet the business goals.

Examples:

- High availability
- Horizontal scalability
- Secure authentication (SSO)
- Encryption in transit and at rest
- API integration with third-party payroll
- Audit logging
- Monitoring and alerting
- Disaster recovery strategy
- Low-latency access for distributed users

---

## Implementation

This is where technologies are selected. Which AWS services implement those capabilities?

Examples:

- Application Load Balancer
- Amazon EC2
- Amazon RDS / Aurora
- Amazon S3
- AWS KMS
- Amazon CloudWatch
- AWS CloudTrail
- Amazon CloudFront (only if justified)
- Amazon Route 53

> **Important:** AWS services are **solutions**, not requirements.
> 

# Common Mistake (What I Learned Today)

❌ My initial instinct was to classify AWS services (e.g., ALB, EC2, CloudFront) as technical requirements.

✅ I learned that:

- Business Requirements define **what** the client needs.
- Technical Requirements define **what capabilities** are required.
- AWS Services define **how** those capabilities are implemented.

---

# Interview Tip

If an interviewer says:

> "Design an HR Management System."
> 

Don't begin with AWS services.

A strong opening is:

> "Before proposing an architecture, I'd like to understand the business objectives, user base, availability expectations, security requirements, integrations, and future growth so I can recommend the most appropriate design."
> 

[EXAMPLE](Requirement%20Engineering%20Business%20vs%20Technical%20vs%20I/EXAMPLE%2039447dc6c74e80f98bede8a0b8e33ed0.md)

![image.png](Requirement%20Engineering%20Business%20vs%20Technical%20vs%20I/image.png)