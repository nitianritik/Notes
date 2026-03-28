# ☁️ AWS Certified Cloud Practitioner (CLF-C02) - Study Notes

**Note:** *These notes are compiled from the AWS Certified Cloud Practitioner course by Stéphane Maarek. Use these notes as a study guide along with hands-on practice and official AWS documentation.* 📚
**Exam Code:** CLF-C02  

---


## 📑 Table of Contents
- [x] [☁️ Cloud Computing Fundamentals](#1-cloud-computing-fundamentals)
- [x] [🔐 AWS Identity & Access Management (IAM)](#2-aws-identity--access-management-iam)
- [x] [🖥️ Amazon EC2](#3-amazon-ec2)
- [x] [💾 EC2 Instance Storage](#4-ec2-instance-storage)
- [x] [⚖️ Elastic Load Balancing & Auto Scaling Groups](#5-elastic-load-balancing--auto-scaling-groups)
- [x] [🪣 Amazon S3](#6-amazon-s3)
- [x] [🗄️ Databases & Analytics](#7-databases--analytics)
- [x] [🐳 Other Compute Services](#8-other-compute-services)
- [x] [🚀 Deploying & Managing Infrastructure at Scale](#9-deploying--managing-infrastructure-at-scale)
- [x] [🌍 Global Infrastructure](#10-global-infrastructure)
- [x] [🔗 Cloud Integration](#11-cloud-integration)
- [x] [📊 Cloud Monitoring](#12-cloud-monitoring)
- [x] [🔒 Amazon VPC](#13-amazon-vpc)
- [x] [🛡️ Security & Compliance](#14-security--compliance)
- [x] [🤖 Machine Learning](#15-machine-learning)
- [x] [💳 Account Management, Billing, & Support](#16-account-management-billing--support)
- [x] [👤 Advanced Identity](#17-advanced-identity)
- [x] [📦 Other AWS Services](#18-other-aws-services)
- [x] [🏗️ AWS Architecting & Ecosystem](#19-aws-architecting--ecosystem)
- [x] [📝 Exam Preparation Tips](#20-exam-preparation-tips)

---

<a id="1-cloud-computing-fundamentals"></a>
## 1. ☁️ Cloud Computing Fundamentals

### What is Cloud Computing?
- **Definition:** On-demand delivery of compute power, database storage, applications, and other IT resources
- **Pricing Model:** 💵 Pay-as-you-go pricing
- **Key Benefits:** ✨
  - Provision exactly the right type and size of computing resources
  - Access as many resources as needed, almost instantly
  - Simple way to access servers, storage, databases, and application services
  - AWS owns and maintains the network-connected hardware

### Deployment Models
1. **🏢 Private Cloud:** Single organization, not exposed to public
   - Complete control
   - Security for sensitive applications
   - Meet specific business needs

2. **🌐 Public Cloud:** Third-party cloud service provider delivered over Internet
   - AWS, Azure, GCP

3. **🔀 Hybrid Cloud:** Combination of on-premises and cloud
   - Control over sensitive assets in private infrastructure
   - Flexibility and cost-effectiveness of public cloud

### Five Characteristics of Cloud Computing
1. **On-demand self-service:** Users provision resources without human interaction
2. **Broad network access:** Resources available over network, diverse client platforms
3. **Multi-tenancy and resource pooling:** Multiple customers share infrastructure with security/privacy
4. **Rapid elasticity and scalability:** Automatically acquire/dispose resources, scale based on demand
5. **Measured service:** Usage is measured, pay for what you use

### Six Advantages of Cloud Computing
1. Trade CAPEX for OPEX (pay on-demand, don't own hardware)
2. Reduced TCO & OPEX
3. Benefit from massive economies of scale
4. Stop guessing capacity - scale based on actual usage
5. Increase speed and agility
6. Go global in minutes - leverage AWS global infrastructure

### Problems Solved by Cloud
- **Flexibility:** Change resource types when needed
- **Cost-Effectiveness:** Pay as you go
- **Scalability:** Accommodate larger loads
- **Elasticity:** Scale out and scale in when needed
- **High-availability and fault-tolerance:** Build across data centers
- **Agility:** Rapidly develop, test, and launch applications

### Types of Cloud Computing
1. **IaaS (Infrastructure as a Service):** 🏗️
   - Building blocks for cloud IT
   - Provides networking, computers, data storage
   - Highest flexibility
   - Examples: EC2, GCP, Azure, Rackspace

2. **PaaS (Platform as a Service):** 📦
   - Removes need to manage underlying infrastructure
   - Focus on deployment and management of applications
   - Examples: Elastic Beanstalk, Heroku, Google App Engine

3. **SaaS (Software as a Service):** 💻
   - Completed product run and managed by service provider
   - Examples: Rekognition, Gmail, Dropbox, Zoom

### AWS Pricing Fundamentals
1. **Compute:** Pay for compute time
2. **Storage:** Pay for data stored in the Cloud
3. **Data Transfer OUT:** Pay for data transfer out (IN is free)

### AWS Cloud Facts 📈
- **2023 Revenue:** $90 billion annual revenue
- **Market Share:** 31% in Q1 2024 (Microsoft 2nd with 25%)
- **Leader:** 13th consecutive year as cloud market leader
- **Users:** Over 1,000,000 active users

---

<a id="2-aws-identity--access-management-iam"></a>
## 2. 🔐 AWS Identity & Access Management (IAM)

### IAM Overview
- **IAM = Identity and Access Management** 🔑
- **Global service** (not region-scoped)
- Root account created by default - **shouldn't be used or shared** ⚠️

### IAM Users & Groups
- **Users:** People within your organization, can be grouped
- **Groups:** Only contain users, not other groups
- Users don't have to belong to a group
- Users can belong to multiple groups

### IAM Policies
- JSON documents that define permissions
- Applied to users or groups
- **Principle:** Apply least privilege - don't give more permissions than needed

### IAM Policy Structure
```json
{
    "Version": "2012-10-17",
    "Statement": [{
        "Effect": "Allow/Deny",
        "Principal": "account/user/role",
        "Action": "list of actions",
        "Resource": "list of resources",
        "Condition": "optional conditions"
    }]
}
```

### IAM Password Policy
- Set minimum password length
- Require specific character types (uppercase, lowercase, numbers, special chars)
- Allow users to change their own passwords
- Require password expiration
- Prevent password re-use

### Multi-Factor Authentication (MFA) 🔒
- **MFA = password you know + security device you own**
- **Benefit:** If password is stolen, account is not compromised
- **MFA Device Options:**
  - Virtual MFA device (Google Authenticator, Authy)
  - Universal 2nd Factor (U2F) Security Key (YubiKey)
  - Hardware Key Fob MFA Device (Gemalto, SurePassID)

### Accessing AWS
1. **AWS Management Console:** Protected by password + MFA
2. **AWS CLI:** Protected by access keys
3. **AWS SDK:** Protected by access keys (for code)

### Access Keys 🔑
- Generated through AWS Console
- Users manage their own access keys
- **Secret - don't share them** 🤫
- Access Key ID ~= username
- Secret Access Key ~= password

### IAM Roles for Services
- Assign permissions to AWS services with IAM Roles
- Common roles:
  - EC2 Instance Roles
  - Lambda Function Roles
  - Roles for CloudFormation

### IAM Security Tools
1. **IAM Credentials Report (account-level):**
   - Lists all account users and status of credentials

2. **IAM Access Advisor (user-level):**
   - Shows service permissions granted to user
   - Shows when services were last accessed
   - Use to revise policies

### IAM Best Practices
- Don't use root account except for AWS account setup
- One physical user = One AWS user
- Assign users to groups, assign permissions to groups
- Create strong password policy
- Use and enforce MFA
- Create and use Roles for AWS services
- Use Access Keys for Programmatic Access (CLI/SDK)
- Audit permissions using IAM Credentials Report & Access Advisor
- Never share IAM users & Access Keys

### Shared Responsibility Model for IAM
**AWS Responsible:**
- Infrastructure (global network security)
- Configuration and vulnerability analysis
- Compliance validation

**You Responsible:**
- Users, Groups, Roles, Policies management
- Enable MFA on all accounts
- Rotate keys often
- Use IAM tools to apply appropriate permissions
- Analyze access patterns & review permissions

---

<a id="3-amazon-ec2"></a>
## 3. 🖥️ Amazon EC2

### EC2 Overview
- **EC2 = Elastic Compute Cloud = Infrastructure as a Service**
- Most popular AWS offering ⭐
- Capabilities:
  - Renting virtual machines (EC2)
  - Storing data on virtual drives (EBS)
  - Distributing load across machines (ELB)
  - Scaling services using Auto Scaling Group (ASG)

### EC2 Sizing & Configuration
- **Operating System:** Linux, Windows, or Mac OS
- **Compute Power:** CPU cores
- **Memory:** RAM
- **Storage:**
  - Network-attached (EBS & EFS)
  - Hardware (EC2 Instance Store)
- **Network Card:** Speed, Public IP address
- **Firewall Rules:** Security groups
- **Bootstrap Script:** EC2 User Data

### EC2 User Data
- Script to bootstrap instances
- Runs **only once** at instance first start
- Runs with **root user**
- Used for:
  - Installing updates
  - Installing software
  - Downloading files from internet
  - Any automation tasks

### EC2 Instance Types
**Naming Convention:** `m5.2xlarge`
- `m`: instance class
- `5`: generation
- `2xlarge`: size within instance class

**Types:**
1. **General Purpose:** Balance of compute, memory, networking
   - Use cases: Web servers, code repositories
   - Example: t2.micro

2. **Compute Optimized:** High performance processors
   - Use cases: Batch processing, media transcoding, HPC, gaming servers

3. **Memory Optimized:** Process large datasets in memory
   - Use cases: High performance databases, in-memory caches, real-time big data

4. **Storage Optimized:** High sequential read/write access
   - Use cases: OLTP systems, NoSQL databases, data warehousing

### Security Groups 🛡️
- **Fundamental of network security in AWS**
- Act as a "firewall" on EC2 instances
- Control traffic into/out of EC2 instances
- **Key Points:** 📌
  - Only contain **allow** rules
  - Can reference by IP or by security group
  - Can be attached to multiple instances
  - Locked to a region/VPC combination
  - Live "outside" the EC2
  - **All inbound traffic blocked by default**
  - **All outbound traffic authorized by default**

### Common Ports 🔌
- **22:** SSH (Secure Shell) - Linux
- **21:** FTP (File Transfer Protocol)
- **22:** SFTP (Secure File Transfer Protocol)
- **80:** HTTP - unsecured websites
- **443:** HTTPS - secured websites
- **3389:** RDP (Remote Desktop Protocol) - Windows

### SSH Access
- **Mac/Linux:** Built-in SSH
- **Windows < 10:** Use PuTTY
- **Windows >= 10:** Built-in SSH
- **Alternative:** EC2 Instance Connect (browser-based, no key file needed)

### EC2 Instance Purchasing Options 💰

1. **On-Demand Instances:** ⏱️
   - Short workload, predictable pricing
   - Pay by second (Linux/Windows) or hour (other OS)
   - Highest cost, no upfront payment
   - No long-term commitment

2. **Reserved Instances:** 📅
   - Up to 72% discount vs On-Demand
   - Reserve specific instance attributes
   - 1 year (+discount) or 3 years (+++discount)
   - Payment: No Upfront, Partial Upfront, All Upfront
   - Scope: Regional or Zonal
   - **Convertible Reserved:** Can change instance type, up to 66% discount

3. **Savings Plans:** 💵
   - Up to 72% discount
   - Commit to usage amount ($10/hour for 1 or 3 years)
   - Locked to instance family & region
   - Flexible across: Instance Size, OS, Tenancy

4. **Spot Instances:** 🎯
   - Up to 90% discount
   - Can be "lost" if max price < current spot price
   - Most cost-efficient
   - Use cases: Batch jobs, data analysis, image processing, flexible workloads
   - **Not suitable for critical jobs or databases**

5. **Dedicated Hosts:** 🏠
   - Physical server fully dedicated to you
   - Address compliance requirements
   - Use existing server-bound software licenses
   - Most expensive option
   - On-demand or Reserved (1 or 3 years)

6. **Dedicated Instances:** 🔒
   - Instances on hardware dedicated to you
   - May share hardware with other instances in same account
   - No control over instance placement

7. **Capacity Reservations:** 📍
   - Reserve On-Demand capacity in specific AZ
   - No time commitment, no billing discounts
   - Charged at On-Demand rate whether running or not

### EC2 Summary 📋
- **EC2 Instance:** AMI (OS) + Instance Size (CPU + RAM) + Storage + Security Groups + EC2 User Data
- **Security Groups:** Firewall attached to EC2 instance
- **EC2 User Data:** Script launched at first start
- **SSH:** Terminal access (port 22)
- **EC2 Instance Role:** Link to IAM roles

---

<a id="4-ec2-instance-storage"></a>
## 4. 💾 EC2 Instance Storage

### EBS Volumes
- **EBS = Elastic Block Store** 📀
- Network drive attached to EC2 instances
- Allows data persistence after termination
- **Key Points:** 📌
  - Can only be mounted to **one instance at a time** (at CCP level)
  - Bound to a **specific Availability Zone**
  - Network drive (not physical) - some latency
  - Can be detached and attached to another instance quickly
  - To move across AZ: first need to snapshot it
  - Provisioned capacity (size in GBs, IOPS)
  - Billed for all provisioned capacity
  - Can increase capacity over time

### EBS Delete on Termination
- Controls EBS behavior when EC2 terminates
- **Default:** Root EBS volume deleted (enabled)
- **Default:** Other attached EBS volumes NOT deleted (disabled)
- Can be controlled via AWS Console/CLI

### EBS Snapshots 📸
- Backup of EBS volume at a point in time
- Not necessary to detach volume (but recommended)
- Can copy snapshots across AZ or Region

### EBS Snapshot Features
- **EBS Snapshot Archive:**
  - Move to "archive tier" - 75% cheaper
  - Restore takes 24-72 hours

- **Recycle Bin for EBS Snapshots:**
  - Retain deleted snapshots
  - Retention: 1 day to 1 year

### AMI (Amazon Machine Image) 🖼️
- Customization of EC2 instance
- Add software, configuration, OS, monitoring
- Faster boot/configuration time
- Built for specific region (can be copied)
- **Types:**
  - Public AMI: AWS provided
  - Your own AMI: You make and maintain
  - AWS Marketplace AMI: Third-party AMI

### AMI Process
1. Start EC2 instance and customize it
2. Stop the instance (for data integrity)
3. Build an AMI (creates EBS snapshots)
4. Launch instances from AMI

### EC2 Image Builder
- Automate creation of VMs or container images
- Automate creation, maintain, validate, test EC2 AMIs
- Can run on schedule
- **Free service** (only pay for underlying resources)

### EC2 Instance Store ⚡
- High-performance hardware disk
- Better I/O performance than EBS
- **Ephemeral:** Lose storage if stopped
- Use cases: Buffer, cache, scratch data, temporary content
- Risk of data loss if hardware fails
- Backups and replication are your responsibility

### EFS (Elastic File System) 📁
- Managed NFS (network file system)
- Can be mounted on **100s of EC2 instances**
- Works with Linux EC2 in **multi-AZ**
- Highly available, scalable
- **Expensive** (3x gp2) 💸
- Pay per use, no capacity planning

### EFS vs EBS
- **EBS:** One instance, locked to AZ
- **EFS:** Multiple instances, multi-AZ

### EFS Infrequent Access (EFS-IA)
- Cost-optimized for files not accessed daily
- Up to 92% lower cost vs EFS Standard
- Automatically moves files based on last access
- Enable with Lifecycle Policy
- Transparent to applications

### Amazon FSx
Launch 3rd party high-performance file systems on AWS

1. **FSx for Windows File Server:**
   - Windows native shared file system
   - SMB protocol & Windows NTFS
   - Integrated with Microsoft Active Directory

2. **FSx for Lustre:**
   - High-performance file storage for HPC
   - Machine Learning, Analytics, Video Processing
   - Scales to 100s GB/s, millions of IOPS, sub-ms latencies

### EC2 Instance Storage Summary 📋
- **EBS volumes:** Network drives, one instance, mapped to AZ
- **EBS Snapshots:** Backups, transfer across AZ
- **AMI:** Ready-to-use EC2 instances with customizations
- **EC2 Image Builder:** Automatically build, test, distribute AMIs
- **EC2 Instance Store:** High performance, ephemeral
- **EFS:** Network file system, multiple instances, multi-AZ
- **EFS-IA:** Cost-optimized for infrequent access
- **FSx for Windows:** Windows file system
- **FSx for Lustre:** HPC Linux file system

---

<a id="5-elastic-load-balancing--auto-scaling-groups"></a>
## 5. ⚖️ Elastic Load Balancing & Auto Scaling Groups

### Scalability & High Availability 📈

**Scalability:** Application/system can handle greater loads by adapting

**Two Types:**
1. **Vertical Scalability:** Increase size of instance
   - Example: t2.micro → t2.large
   - Common for non-distributed systems (databases)
   - Limited by hardware

2. **Horizontal Scalability:** Increase number of instances
   - Common for web applications
   - Easy with cloud offerings like EC2

**High Availability:**
- Run application in at least **2 Availability Zones**
- Goal: Survive data center loss (disaster)

### Scalability vs Elasticity vs Agility

- **Scalability:** Ability to accommodate larger load (scale up/out)
- **Elasticity:** Auto-scaling based on load (cloud-friendly, pay-per-use)
- **Agility:** New IT resources available quickly (weeks → minutes)

### Load Balancing
- Servers that forward internet traffic to multiple servers (EC2 instances)
- **Benefits:**
  - Spread load across multiple instances
  - Single point of access (DNS)
  - Handle failures of downstream instances
  - Health checks
  - SSL termination (HTTPS)
  - High availability across zones

### Elastic Load Balancer (ELB) ⚖️
- **Managed load balancer**
- AWS guarantees it will work
- AWS handles upgrades, maintenance, high availability
- **4 Types:** 📌

1. **Application Load Balancer (ALB):** 🌐
   - HTTP/HTTPS/gRPC (Layer 7)
   - HTTP routing features
   - Static DNS (URL)

2. **Network Load Balancer (NLB):** 📡
   - TCP/UDP (Layer 4)
   - High performance: millions of requests/second
   - Static IP through Elastic IP

3. **Gateway Load Balancer (GWLB):** 🚪
   - GENEVE Protocol on IP Packets (Layer 3)
   - Route traffic to firewalls on EC2 instances
   - Intrusion detection

4. **Classic Load Balancer:** 📜
   - Retired in 2023
   - Layer 4 & 7

### Auto Scaling Groups (ASG)
- **Goal:**
  - Scale out (add instances) to match increased load
  - Scale in (remove instances) to match decreased load
  - Ensure minimum and maximum machines running
  - Automatically register new instances to load balancer
  - Replace unhealthy instances
  - Cost savings: run at optimal capacity

### ASG Scaling Strategies

1. **Manual Scaling:** Update size manually

2. **Dynamic Scaling:**
   - **Simple/Step Scaling:** Based on CloudWatch alarms
   - **Target Tracking Scaling:** Maintain average metric (e.g., CPU at 40%)
   - **Scheduled Scaling:** Anticipate based on known patterns

3. **Predictive Scaling:**
   - Uses Machine Learning to predict future traffic
   - Automatically provisions instances in advance
   - Useful for predictable time-based patterns

### ELB & ASG Summary 📋
- **High Availability vs Scalability vs Elasticity vs Agility**
- **ELB:** Distribute traffic, Multi-AZ, health checks
- **4 Types:** Classic (old), ALB (HTTP-L7), NLB (TCP-L4), GWLB (L3)
- **ASG:** Implement elasticity, Multi-AZ, scale based on demand, replace unhealthy instances
- **Integration:** ASG integrated with ELB

---

<a id="6-amazon-s3"></a>
## 6. 🪣 Amazon S3

### S3 Overview
- **S3 = Simple Storage Service** 🪣
- One of main building blocks of AWS
- "Infinitely scaling" storage ♾️
- Many websites use S3 as backbone
- Many AWS services integrate with S3

### S3 Use Cases
- Backup and storage
- Disaster Recovery
- Archive
- Hybrid Cloud storage
- Application hosting
- Media hosting
- Data lakes & big data analytics
- Software delivery
- Static website

### S3 Buckets
- Store objects (files) in "buckets" (directories)
- **Globally unique name** (across all regions, all accounts)
- Defined at **region level**
- **Naming Convention:**
  - No uppercase, no underscore
  - 3-63 characters long
  - Not an IP
  - Must start with lowercase letter or number
  - Must NOT start with prefix `xn--`
  - Must NOT end with suffix `-s3alias`

### S3 Objects
- Objects have a **Key** (full path)
- Example: `s3://my-bucket/my_folder1/another_folder/my_file.txt`
- Key = prefix + object name
- **No concept of "directories"** (just keys with slashes)
- **Max Object Size:** 5TB (5000GB)
- If uploading > 5GB, must use "multi-part upload"
- **Metadata:** System or user metadata
- **Tags:** Unicode key/value pairs (up to 10)
- **Version ID:** If versioning enabled

### S3 Security

**User-Based:**
- IAM Policies - API calls allowed for IAM user

**Resource-Based:**
- Bucket Policies - bucket-wide rules, allows cross-account
- Object ACL - finer grain (can be disabled)
- Bucket ACL - less common (can be disabled)

**Access Rule:**
- IAM principal can access if:
  - User IAM permissions ALLOW it OR resource policy ALLOWS it
  - AND there's no explicit DENY

**Encryption:** Encrypt objects using encryption keys

### S3 Bucket Policies
- JSON-based policies
- Resources: buckets and objects
- Effect: Allow/Deny
- Actions: Set of API to Allow/Deny
- Principal: Account or user to apply policy to
- **Use cases:**
  - Grant public access
  - Force objects to be encrypted at upload
  - Grant cross-account access

### Block Public Access Settings
- Prevent company data leaks
- If bucket should never be public, leave these on
- Can be set at account level

### S3 Static Website Hosting
- Host static websites accessible on Internet
- URL format: `http://bucket-name.s3-website-aws-region.amazonaws.com`
- **403 Forbidden:** Make sure bucket policy allows public reads!

### S3 Versioning
- Enable at **bucket level**
- Same key overwrite changes version: 1, 2, 3...
- **Best practice:** Version your buckets
- **Benefits:**
  - Protect against unintended deletes
  - Ability to restore version
  - Easy rollback to previous version
- **Notes:**
  - Files not versioned before enabling have version "null"
  - Suspending versioning does NOT delete previous versions

### S3 Replication
- **Must enable Versioning** in source and destination
- **Cross-Region Replication (CRR):** Different regions
- **Same-Region Replication (SRR):** Same region
- Buckets can be in different AWS accounts
- Copying is **asynchronous**
- Must give proper IAM permissions to S3
- **Use cases:**
  - CRR: Compliance, lower latency access, replication across accounts
  - SRR: Log aggregation, live replication between production/test

### S3 Storage Classes 📦

1. **S3 Standard:** ⭐
   - 99.99% Availability
   - Frequently accessed data
   - Low latency, high throughput
   - Sustain 2 concurrent facility failures

2. **S3 Standard-IA (Infrequent Access):** 📥
   - 99.9% Availability
   - Less frequently accessed, rapid access when needed
   - Lower cost than Standard
   - Use cases: Disaster Recovery, backups

3. **S3 One Zone-IA:** 📍
   - 99.5% Availability
   - High durability in single AZ
   - Data lost when AZ destroyed
   - Use cases: Secondary backup copies, recreatable data

4. **S3 Glacier Instant Retrieval:** ❄️
   - Millisecond retrieval
   - Data accessed once a quarter
   - Minimum storage duration: 90 days

5. **S3 Glacier Flexible Retrieval:** 🧊
   - Expedited (1-5 min), Standard (3-5 hours), Bulk (5-12 hours - free)
   - Minimum storage duration: 90 days

6. **S3 Glacier Deep Archive:** 🏔️
   - Long-term storage
   - Standard (12 hours), Bulk (48 hours)
   - Minimum storage duration: 180 days

7. **S3 Intelligent-Tiering:** 🧠
   - Small monthly monitoring fee
   - Automatically moves objects between tiers based on usage
   - No retrieval charges
   - Tiers: Frequent, Infrequent (30 days), Archive Instant (90 days), Archive (90-700+ days), Deep Archive (180-700+ days)

8. **S3 Express One Zone:** ⚡
   - High performance, single AZ
   - Directory Bucket (single AZ)
   - 100,000s requests/second, single-digit ms latency
   - Up to 10x better performance than Standard (50% lower costs)
   - 99.95% Availability
   - Use cases: Latency-sensitive apps, AI/ML training, financial modeling

### S3 Durability and Availability
- **Durability:** 99.999999999% (11 9's) across multiple AZ
- Same for all storage classes
- **Availability:** Varies by storage class
  - S3 Standard: 99.99% (53 minutes unavailable per year)

### S3 Encryption
- **Server-Side Encryption:** Server encrypts file after receiving
- **Client-Side Encryption:** Encrypt file before uploading

### IAM Access Analyzer for S3
- Ensures only intended people have access
- Evaluates Bucket Policies, ACLs, Access Point Policies
- Powered by IAM Access Analyzer

### Shared Responsibility Model for S3
**AWS Responsible:**
- Infrastructure (global security, durability, availability)
- Configuration and vulnerability analysis
- Compliance validation

**You Responsible:**
- S3 Versioning
- S3 Bucket Policies
- S3 Replication Setup
- Logging and Monitoring
- S3 Storage Classes
- Data encryption at rest and in transit

### AWS Snowball
- Highly-secure, portable devices for data collection/processing
- Migrate up to Petabytes of data
- **Types:**
  - Snowball Edge Storage Optimized: 104 vCPUs, 416 GB, 210 TB
  - Snowball Edge Compute Optimized: 104 vCPUs, 416 GB, 28 TB
- **Use case:** If transfer takes more than a week over network, use Snowball

### Edge Computing with Snowball
- Process data at edge locations (truck, ship, mining station)
- Limited internet, no computing power
- Run EC2 Instances or Lambda functions at edge
- Use cases: Preprocess data, machine learning, transcoding media

### AWS Storage Gateway
- Bridge between on-premise data and cloud data in S3
- Hybrid storage service
- **Use cases:** Disaster recovery, backup & restore, tiered storage
- **Types:**
  - File Gateway
  - Volume Gateway
  - Tape Gateway

### S3 Summary 📋
- **Buckets vs Objects:** Globally unique name, tied to region
- **Security:** IAM policy, Bucket Policy, Encryption
- **Static Websites:** Host on S3
- **Versioning:** Multiple versions, prevent accidental deletes
- **Replication:** Same-region or cross-region, must enable versioning
- **Storage Classes:** Standard, IA, 1Z-IA, Intelligent, Glacier (Instant, Flexible, Deep), Express One Zone
- **Snowball:** Import data via physical device, edge computing
- **Storage Gateway:** Hybrid solution for on-premises storage

---

<a id="7-databases--analytics"></a>
## 7. 🗄️ Databases & Analytics

### Database Types 🗃️

**Relational Databases (SQL):** 📊
- Looks like Excel spreadsheets with links
- Use SQL language
- Examples: MySQL, PostgreSQL, Oracle, SQL Server

**NoSQL Databases:** 📄
- Non-relational databases
- Purpose-built for specific data models
- Flexible schemas
- **Benefits:**
  - Flexibility: Easy to evolve data model
  - Scalability: Scale-out with distributed clusters
  - High-performance: Optimized for specific data model
- **Types:** Key-value, document, graph, in-memory, search

### AWS Database Benefits
- Quick Provisioning
- High Availability
- Vertical and Horizontal Scaling
- Automated Backup & Restore
- Operations and Upgrades handled by AWS
- OS Patching handled by AWS
- Monitoring and alerting

### Amazon RDS (Relational Database Service) 🗄️
- Managed DB service for SQL databases
- **Supported:** ✅
  - PostgreSQL
  - MySQL
  - MariaDB
  - Oracle
  - Microsoft SQL Server
  - IBM DB2
  - **Aurora** (AWS Proprietary)

### RDS Advantages vs EC2
- Automated provisioning, OS patching
- Continuous backups and restore to specific timestamp (Point in Time Restore)
- Monitoring dashboards
- Read replicas for improved read performance
- Multi-AZ setup for Disaster Recovery
- Maintenance windows for upgrades
- Scaling capability (vertical and horizontal)
- Storage backed by EBS
- **BUT:** Can't SSH into instances

### Amazon Aurora
- Proprietary technology from AWS
- Supports PostgreSQL and MySQL
- **Performance:** 5x improvement over MySQL on RDS, 3x over Postgres on RDS
- Storage automatically grows in 10GB increments, up to 256 TB
- Costs 20% more than RDS but more efficient

### Aurora Serverless
- Automated database instantiation and auto-scaling
- Supports PostgreSQL and MySQL
- No capacity planning needed
- Pay per second
- Use cases: Infrequent, intermittent, unpredictable workloads

### RDS Deployments

**Read Replicas:**
- Scale read workload
- Up to 15 Read Replicas
- Data only written to main DB

**Multi-AZ:**
- Failover in case of AZ outage (high availability)
- Data only read/written to main database
- Only 1 other AZ as failover

**Multi-Region (Read Replicas):**
- Disaster recovery in case of region issue
- Local performance for global reads
- Replication cost

### Amazon ElastiCache
- Managed Redis or Memcached
- In-memory databases with high performance, low latency
- Reduces load off databases for read-intensive workloads
- AWS handles: OS maintenance, patching, optimizations, setup, configuration, monitoring, failure recovery, backups

### Amazon DynamoDB ⚡
- Fully Managed, Highly available with replication across 3 AZ
- **NoSQL** database (key/value)
- **Features:** ✨
  - Scales to massive workloads
  - Distributed "serverless" database
  - Millions of requests/second, trillions of rows, 100s of TB
  - Fast and consistent performance
  - Single-digit millisecond latency
  - Integrated with IAM
  - Low cost and auto-scaling
  - Standard & Infrequent Access (IA) Table Class

### DynamoDB Accelerator (DAX)
- Fully Managed in-memory cache for DynamoDB
- **10x performance improvement**
- Single-digit ms → microseconds latency
- Secure, highly scalable, highly available
- **Difference from ElastiCache:** DAX only for DynamoDB, ElastiCache for other databases

### DynamoDB Global Tables
- Make table accessible with low latency in multiple regions
- **Active-Active replication** (read/write to any region)

### Amazon Redshift
- Based on PostgreSQL
- **OLAP** (Online Analytical Processing) - analytics and data warehousing
- Not for OLTP
- **Features:**
  - 10x better performance than other data warehouses
  - Scale to Petabytes
  - Columnar storage
  - Massively Parallel Query Execution (MPP)
  - Highly available
  - Pay as you go
  - SQL interface
  - Integrates with BI tools (QuickSight, Tableau)

### Redshift Serverless
- Automatically provisions and scales data warehouse capacity
- Run analytics without managing infrastructure
- Pay only for what you use
- Use cases: Reporting, dashboarding, real-time analytics

### Amazon EMR
- **EMR = Elastic MapReduce**
- Helps create Hadoop clusters (Big Data)
- Analyze and process vast amounts of data
- Clusters can be hundreds of EC2 instances
- Also supports: Apache Spark, HBase, Presto, Flink
- Auto-scaling, integrated with Spot instances
- **Use cases:** Data processing, machine learning, web indexing, big data

### Amazon Athena 🔍
- **Serverless** query service to analyze data in S3
- Uses standard SQL
- Supports: CSV, JSON, ORC, Avro, Parquet
- **Pricing:** $5.00 per TB of data scanned
- Use compressed or columnar data for cost-savings
- **Use cases:** BI/analytics/reporting, analyze VPC Flow Logs, ELB Logs, CloudTrail trails
- **Exam Tip:** Analyze data in S3 using serverless SQL → use Athena 💡

### Amazon QuickSight
- Serverless ML-powered business intelligence service
- Create interactive dashboards
- Fast, automatically scalable, embeddable
- Per-session pricing
- **Use cases:** Business analytics, visualizations, ad-hoc analysis, business insights
- Integrates with: RDS, Aurora, Athena, Redshift, S3

### DocumentDB
- AWS implementation of MongoDB (NoSQL)
- Store, query, index JSON data
- Similar deployment concepts as Aurora
- Fully Managed, highly available across 3 AZ
- Storage automatically grows in 10GB increments
- Scales to millions of requests/second

### Amazon Neptune
- Fully managed **graph database**
- **Use cases:** Social networks, knowledge graphs, fraud detection, recommendation engines
- Highly available across 3 AZ, up to 15 read replicas
- Store billions of relations, query with milliseconds latency

### Amazon Timestream
- Fully managed, fast, scalable, serverless **time series database**
- Automatically scales up/down
- Store and analyze trillions of events per day
- 1000x faster, 1/10th cost of relational databases
- Built-in time series analytics functions

### Amazon Managed Blockchain
- Managed service to:
  - Join public blockchain networks
  - Create scalable private networks
- Compatible with: Hyperledger Fabric & Ethereum

### AWS Glue
- Managed **ETL** (Extract, Transform, Load) service
- Prepare and transform data for analytics
- Fully serverless
- **Glue Data Catalog:** Catalog of datasets
- Used by: Athena, Redshift, EMR

### DMS (Database Migration Service)
- Quickly and securely migrate databases to AWS
- Resilient, self-healing
- Source database remains available during migration
- **Supports:**
  - Homogeneous: Oracle → Oracle
  - Heterogeneous: SQL Server → Aurora

### Databases & Analytics Summary 📋
- **Relational (OLTP):** RDS & Aurora (SQL)
- **Multi-AZ vs Read Replicas vs Multi-Region**
- **In-memory:** ElastiCache
- **Key/Value:** DynamoDB (serverless) & DAX (cache)
- **Warehouse (OLAP):** Redshift (SQL)
- **Hadoop Cluster:** EMR
- **Query S3:** Athena (serverless SQL)
- **Dashboards:** QuickSight (serverless)
- **MongoDB:** DocumentDB
- **Blockchain:** Managed Blockchain
- **ETL:** Glue
- **Migration:** DMS
- **Graph:** Neptune
- **Time Series:** Timestream

---

---

<a id="8-other-compute-services"></a>
## 8. 🐳 Other Compute Services

### Docker Overview 🐳
- Software development platform to deploy apps
- Apps packaged in containers that run on any OS
- **Benefits:** ✨
  - Apps run the same regardless of where they're run
  - No compatibility issues
  - Predictable behavior
  - Less work, easier to maintain and deploy
  - Works with any language, OS, technology
  - Scale containers up/down quickly (seconds)

### Docker Images Storage
- **Public:** Docker Hub (https://hub.docker.com/)
- **Private:** Amazon ECR (Elastic Container Registry)

### Docker vs Virtual Machines
- Docker shares resources with host → many containers on one server
- VMs have separate guest OS for each VM

### Amazon ECS (Elastic Container Service)
- Launch Docker containers on AWS
- **You must provision & maintain** the infrastructure (EC2 instances)
- AWS takes care of starting/stopping containers
- Has integrations with Application Load Balancer

### AWS Fargate
- Launch Docker containers on AWS
- **You do NOT provision** the infrastructure (no EC2 instances to manage)
- **Serverless offering**
- AWS runs containers based on CPU/RAM you need

### Amazon ECR (Elastic Container Registry)
- Private Docker Registry on AWS
- Store Docker images to run by ECS or Fargate

### Amazon EKS (Elastic Kubernetes Service)
- Launch managed Kubernetes clusters on AWS
- Kubernetes: open-source system for management, deployment, scaling of containerized apps
- Containers can be hosted on:
  - EC2 instances
  - Fargate (Serverless)
- Kubernetes is cloud-agnostic (works in any cloud)

### What is Serverless?
- Developers don't manage servers
- Just deploy code/functions
- Initially: Serverless == FaaS (Function as a Service)
- Now includes: databases, messaging, storage (anything managed)
- **Note:** There are still servers, you just don't manage/provision/see them

### AWS Lambda λ
- **Virtual functions** - no servers to manage
- Limited by time (short executions)
- Run on-demand
- Scaling is automated ⚡

### Lambda Benefits
- **Easy Pricing:** Pay per request and compute time
- **Free Tier:** 1,000,000 requests and 400,000 GB-seconds compute time
- Integrated with whole AWS suite
- Event-driven: functions invoked by AWS when needed
- Integrated with many programming languages
- Easy monitoring through CloudWatch
- Up to 10GB of RAM (increasing RAM improves CPU and network)

### Lambda Language Support
- Node.js (JavaScript)
- Python
- Java
- C# (.NET Core) / PowerShell
- Ruby
- Custom Runtime API (Rust, Golang, etc.)
- Lambda Container Image

### Lambda Pricing
- **Pay per calls:**
  - First 1,000,000 requests free
  - $0.20 per 1 million requests thereafter
- **Pay per duration:** (increment of 1 ms)
  - 400,000 GB-seconds compute time per month FREE
  - After that $1.00 for 600,000 GB-seconds

### Lambda Use Cases
- Create thumbnails for images uploaded to S3
- Run serverless cron jobs
- API Gateway: expose Lambda functions as HTTP API

### Amazon API Gateway
- Fully managed service to create, publish, maintain, monitor, secure APIs
- Serverless and scalable
- Supports RESTful APIs and WebSocket APIs
- Features: Security, user authentication, API throttling, API keys, monitoring

### AWS Batch
- Fully managed batch processing at any scale
- Run 100,000s of computing batch jobs on AWS
- **Batch job:** Job with start and end (not continuous)
- Dynamically launches EC2 instances or Spot Instances
- Provisions right amount of compute/memory
- Batch jobs defined as Docker images, run on ECS

### Batch vs Lambda
- **Lambda:**
  - Time limit
  - Limited runtimes
  - Limited temporary disk space
  - Serverless
- **Batch:**
  - No time limit
  - Any runtime (Docker image)
  - Rely on EBS/instance store for disk space
  - Relies on EC2 (can be managed by AWS)

### Amazon Lightsail
- Virtual servers, storage, databases, networking
- Low & predictable pricing
- Simpler alternative to EC2, RDS, ELB, EBS, Route 53
- Great for people with little cloud experience
- **Use cases:**
  - Simple web applications (LAMP, Nginx, MEAN, Node.js templates)
  - Websites (WordPress, Magento, Plesk, Joomla templates)
  - Dev/Test environment
- **Limitations:** High availability but no auto-scaling, limited AWS integrations

### Other Compute Summary 📋
- **Docker:** Container technology
- **ECS:** Run Docker containers on EC2 instances
- **Fargate:** Run Docker containers without provisioning infrastructure (serverless)
- **ECR:** Private Docker Images Repository
- **EKS:** Managed Kubernetes
- **Lambda:** Serverless, Function as a Service, seamless scaling, reactive
- **Batch:** Run batch jobs on AWS across managed EC2 instances
- **Lightsail:** Predictable & low pricing for simple application & DB stacks

---

<a id="9-deploying--managing-infrastructure-at-scale"></a>
## 9. 🚀 Deploying & Managing Infrastructure at Scale

### AWS CloudFormation 📋
- **Declarative way** of outlining AWS Infrastructure
- Supports most AWS resources
- CloudFormation creates resources in right order with exact configuration

### CloudFormation Benefits
- **Infrastructure as Code:**
  - No resources manually created
  - Changes reviewed through code
- **Cost:**
  - Resources tagged with identifier
  - Estimate costs using template
  - Automation: Delete templates at 5 PM, recreate at 8 AM (Dev)
- **Productivity:**
  - Destroy and re-create infrastructure on the fly
  - Automated diagram generation
  - Declarative programming (no orchestration needed)
  - Leverage existing templates
- **Supports:** Almost all AWS resources

### AWS Cloud Development Kit (CDK)
- Define cloud infrastructure using familiar language:
  - JavaScript/TypeScript, Python, Java, .NET
- Code is "compiled" into CloudFormation template (JSON/YAML)
- Deploy infrastructure and application runtime code together
- Great for Lambda functions and Docker containers in ECS/EKS

### AWS Elastic Beanstalk
- **Developer-centric view** of deploying application on AWS
- Uses: EC2, ASG, ELB, RDS, etc.
- **Platform as a Service (PaaS)**
- **Free** (pay for underlying instances)
- **Managed service:**
  - Instance configuration/OS handled by Beanstalk
  - Deployment strategy configurable
  - Capacity provisioning
  - Load balancing & auto-scaling
  - Application health-monitoring
- **Developer responsibility:** Just the application code

### Elastic Beanstalk Architecture Models
1. **Single Instance:** Good for dev
2. **LB + ASG:** Great for production/pre-production web applications
3. **ASG only:** Great for non-web apps (workers, etc.)

### Elastic Beanstalk Supported Platforms
- Go, Java SE, Java with Tomcat
- .NET on Windows Server with IIS
- Node.js, PHP, Python, Ruby
- Packer Builder
- Single Container Docker
- Multi-Container Docker
- Preconfigured Docker

### AWS CodeDeploy
- Deploy application automatically
- Works with EC2 Instances
- Works with On-Premises Servers
- **Hybrid service**
- Servers/Instances must be provisioned and configured ahead of time with CodeDeploy Agent

### AWS CodeCommit
- Source-control service that hosts Git-based repositories
- AWS competing product to GitHub
- **Benefits:**
  - Fully managed
  - Scalable & highly available
  - Private, Secured, Integrated with AWS

### AWS CodeBuild
- Code building service in the cloud
- Compiles source code, runs tests, produces ready-to-deploy packages
- **Benefits:**
  - Fully managed, serverless
  - Continuously scalable & highly available
  - Secure
  - Pay-as-you-go (only pay for build time)

### AWS CodePipeline
- Orchestrate steps to automatically push code to production
- Code => Build => Test => Provision => Deploy
- **Basis for CI/CD** (Continuous Integration & Continuous Delivery)
- **Benefits:**
  - Fully managed
  - Compatible with: CodeCommit, CodeBuild, CodeDeploy, Elastic Beanstalk, CloudFormation, GitHub, 3rd-party services, custom plugins
  - Fast delivery & rapid updates

### AWS CodeArtifact
- Secure, scalable, cost-effective artifact management
- Store and retrieve code dependencies
- Works with: Maven, Gradle, npm, yarn, twine, pip, NuGet
- Developers and CodeBuild can retrieve dependencies from CodeArtifact

### AWS Systems Manager (SSM)
- Manage EC2 and On-Premises systems at scale
- **Hybrid AWS service**
- Get operational insights about infrastructure state
- **Suite of 10+ products:**
  - Patching automation for compliance
  - Run commands across entire fleet of servers
  - Store parameter configuration (SSM Parameter Store)
- Works for: Linux, Windows, MacOS, Raspberry Pi OS

### SSM Agent
- Installed on systems to control
- Installed by default on Amazon Linux AMI & some Ubuntu AMI
- If instance can't be controlled with SSM → SSM agent issue

### SSM Session Manager
- Start secure shell on EC2 and on-premises servers
- **No SSH access, bastion hosts, or SSH keys needed**
- **No port 22 needed** (better security)
- Supports: Linux, macOS, Windows
- Send session log data to S3 or CloudWatch Logs

### SSM Parameter Store
- Secure storage for configuration and secrets
- API Keys, passwords, configurations
- Serverless, scalable, durable, easy SDK
- Control access using IAM
- Version tracking & encryption (optional)

### Deployment Summary 📋
- **CloudFormation:** Infrastructure as Code (AWS only)
- **Beanstalk:** Platform as a Service (PaaS), limited to certain languages/Docker
- **CodeDeploy:** Deploy & upgrade applications onto servers (hybrid)
- **Systems Manager:** Patch, configure, run commands at scale (hybrid)

### Developer Services Summary 📋
- **CodeCommit:** Store code in private git repository
- **CodeBuild:** Build & test code in AWS
- **CodeDeploy:** Deploy code onto servers
- **CodePipeline:** Orchestration of pipeline (code to build to deploy)
- **CodeArtifact:** Store software packages/dependencies
- **AWS CDK:** Define cloud infrastructure using programming language

---

<a id="10-global-infrastructure"></a>
## 10. 🌍 Global Infrastructure

### Why Make a Global Application?
1. **Decreased Latency:**
   - Deploy applications closer to users
   - Better user experience

2. **Disaster Recovery (DR):**
   - If AWS region goes down, fail-over to another region
   - Increase application availability

3. **Attack Protection:**
   - Distributed global infrastructure is harder to attack

### Global AWS Infrastructure
- **Regions:** Deploy applications and infrastructure
- **Availability Zones:** Multiple data centers
- **Edge Locations (Points of Presence):** Content delivery close to users

### Global Applications in AWS
1. **Global DNS:** Route 53
   - Route users to closest deployment with least latency
   - Great for disaster recovery strategies

2. **Global CDN:** CloudFront
   - Replicate application to AWS Edge Locations
   - Decrease latency, cache common requests

3. **S3 Transfer Acceleration:**
   - Accelerate global uploads & downloads into S3

4. **AWS Global Accelerator:**
   - Improve global application availability and performance using AWS global network

### Amazon Route 53 🗺️
- **Managed DNS** (Domain Name System)
- DNS: Collection of rules and records to reach servers through URLs
- **Common Records:** 📌
  - **A record:** hostname to IPv4 (www.google.com => 12.34.56.78)
  - **AAAA record:** hostname to IPv6
  - **CNAME:** hostname to hostname (search.google.com => www.google.com)
  - **Alias:** hostname to AWS resource (ELB, CloudFront, S3, RDS, etc.)

### Route 53 Routing Policies
1. **Simple Routing Policy:** No health checks
2. **Weighted Routing Policy:** Distribute traffic based on weights
3. **Latency Routing Policy:** Route to region with least latency
4. **Failover Routing Policy:** Disaster recovery (primary/failover with health check)

### Amazon CloudFront 🌐
- **Content Delivery Network (CDN)**
- Improves read performance, content cached at edge
- Improves user experience
- Hundreds of Points of Presence globally
- **DDoS protection** (worldwide), integration with Shield, WAF 🛡️

### CloudFront Origins
1. **S3 bucket:**
   - Distribute files and cache at edge
   - Upload files to S3 through CloudFront
   - Secured using Origin Access Control (OAC)

2. **VPC Origin:**
   - Applications hosted in VPC private subnets
   - Private ALB/NLB/EC2 Instances

3. **Custom Origin (HTTP):**
   - S3 website (must enable bucket as static S3 website)
   - Any public HTTP backend (e.g., Public ALB)

### CloudFront vs S3 Cross Region Replication
- **CloudFront:**
  - Global Edge network
  - Files cached for TTL (maybe a day)
  - Great for static content available everywhere

- **S3 Cross Region Replication:**
  - Setup for each region
  - Files updated in near real-time
  - Read only
  - Great for dynamic content at low-latency in few regions

### S3 Transfer Acceleration
- Increase transfer speed by transferring file to AWS edge location
- Edge location forwards data to S3 bucket in target region

### AWS Global Accelerator
- Improve global application availability and performance using AWS global network
- Leverage AWS internal network to optimize route (60% improvement)
- 2 Anycast IP created for application
- Traffic sent through Edge Locations
- Edge locations send traffic to application

### Global Accelerator vs CloudFront
- **Both use AWS global network and edge locations**
- **Both integrate with AWS Shield for DDoS protection**
- **CloudFront:**
  - Content Delivery Network
  - Improves performance for cacheable content (images, videos)
  - Content served at edge
- **Global Accelerator:**
  - No caching, proxying packets at edge to applications
  - Improves performance for wide range of applications over TCP/UDP
  - Good for HTTP use cases requiring static IP addresses
  - Good for HTTP use cases requiring deterministic, fast regional failover

### AWS Outposts
- **Hybrid Cloud:** On-premises infrastructure alongside cloud
- Outposts are "server racks" offering same AWS infrastructure, services, APIs & tools
- AWS sets up and manages "Outposts Racks" within your on-premises infrastructure
- **You are responsible for Outposts Rack physical security**
- **Benefits:**
  - Low-latency access to on-premises systems
  - Local data processing
  - Data residency
  - Easier migration from on-premises to cloud
  - Fully managed service
- **Services that work on Outposts:**
  - EC2, EBS, S3, EKS, ECS, RDS, EMR

### AWS WaveLength
- WaveLength Zones: Infrastructure deployments embedded in telecom providers' datacenters at edge of 5G networks
- Brings AWS services to edge of 5G networks
- Example: EC2, EBS, VPC
- **Ultra-low latency** applications through 5G networks
- Traffic doesn't leave Communication Service Provider's (CSP) network
- High-bandwidth and secure connection to parent AWS Region
- **Use cases:** Smart Cities, ML-assisted diagnostics, Connected Vehicles, Interactive Live Video Streams, AR/VR, Real-time Gaming

### AWS Local Zones
- Places AWS compute, storage, database, other selected services closer to end users
- **Extension of an AWS Region**
- Compatible with: EC2, RDS, ECS, EBS, ElastiCache, Direct Connect
- **Example:**
  - AWS Region: N. Virginia (us-east-1)
  - AWS Local Zones: Boston, Chicago, Dallas, Houston, Miami

### Global Applications Architecture
1. **Single Region, Single AZ:** Basic setup
2. **Single Region, Multi AZ:** High Availability
3. **Multi Region, Active-Passive:** Global reads' latency, global writes' latency
4. **Multi Region, Active-Active:** Reads' latency, writes' latency

### Global Applications Summary 📋
- **Route 53:** Global DNS, route users to closest deployment, disaster recovery
- **CloudFront:** Global CDN, replicate to Edge Locations, decrease latency, cache requests
- **S3 Transfer Acceleration:** Accelerate global uploads/downloads
- **Global Accelerator:** Improve global application availability and performance
- **Outposts:** Deploy Outposts Racks in Data Centers to extend AWS services
- **WaveLength:** Bring AWS services to edge of 5G networks, ultra-low latency
- **Local Zones:** Bring AWS resources closer to users, latency-sensitive applications

---

<a id="11-cloud-integration"></a>
## 11. 🔗 Cloud Integration

### Application Communication Patterns
1. **Synchronous:** Application to application
2. **Asynchronous/Event-based:** Application to queue to application

### Why Decouple Applications?
- Synchronous can be problematic with traffic spikes
- Better to decouple using:
  - **SQS:** Queue model
  - **SNS:** Pub/sub model
  - **Kinesis:** Real-time data streaming model
- These services can scale independently

### Amazon SQS (Simple Queue Service) 📬
- **Queue:** Producer sends messages, Consumer polls messages
- **Standard Queue:** 📋
  - Oldest AWS offering (over 10 years old)
  - Fully managed service (~serverless)
  - Scales from 1 message/second to 10,000s/second
  - Default retention: 4 days, maximum 14 days
  - No limit to messages in queue
  - Messages deleted after read by consumers
  - Low latency (<10 ms on publish and receive)
  - Consumers share work to read messages & scale horizontally

### SQS FIFO Queue
- **FIFO = First In First Out**
- Messages processed in order by consumer

### Amazon Kinesis Data Streams
- **Real-time big data streaming**
- Managed service to collect, process, analyze real-time streaming data at any scale
- **Amazon Kinesis Data Streams:** Low latency streaming to ingest data at scale
- **Amazon Data Firehose:** Load Kinesis Data Streams into S3, Redshift, OpenSearch, etc.

### Amazon SNS (Simple Notification Service) 📢
- **Pub/Sub model:** Send one message to many receivers
- Event publishers send message to one SNS topic
- Many event subscribers listen to SNS topic notifications
- Each subscriber gets all messages
- **Up to 12,500,000 subscriptions per topic, 100,000 topics limit**
- **Subscribers:**
  - SQS, Lambda, Amazon Data Firehose
  - HTTP(S) Endpoints
  - SMS & Mobile Notifications
  - Emails

### Amazon MQ
- **Managed message broker service**
- For traditional applications using open protocols: MQTT, AMQP, STOMP, Openwire, WSS
- Instead of re-engineering to use SQS/SNS, use Amazon MQ
- **Doesn't scale as much as SQS/SNS**
- Runs on servers, can run in Multi-AZ with failover
- Has both queue feature (~SQS) and topic features (~SNS)

### Integration Summary 📋
- **SQS:** Queue service, multiple producers/consumers, messages kept up to 14 days, decouple applications
- **SNS:** Notification service, multiple subscribers, send all messages to all, no message retention
- **Kinesis:** Real-time data streaming, persistence and analysis
- **Amazon MQ:** Managed message broker for ActiveMQ and RabbitMQ (MQTT, AMQP protocols)

---

<a id="12-cloud-monitoring"></a>
## 12. 📊 Cloud Monitoring

### Amazon CloudWatch Metrics 📈
- CloudWatch provides metrics for every service in AWS
- **Metric:** Variable to monitor (CPUUtilization, NetworkIn...)
- Metrics have timestamps
- Can create CloudWatch dashboards of metrics

### Important Metrics
- **EC2 instances:** CPU Utilization, Status Checks, Network (not RAM)
  - Default: every 5 minutes
  - Detailed Monitoring ($$$): every 1 minute
- **EBS volumes:** Disk Read/Writes
- **S3 buckets:** BucketSizeBytes, NumberOfObjects, AllRequests
- **Billing:** Total Estimated Charge (only in us-east-1)
- **Service Limits:** How much you've been using a service API
- **Custom metrics:** Push your own metrics

### Amazon CloudWatch Alarms 🔔
- Trigger notifications for any metric
- **Alarm Actions:** ⚡
  - Auto Scaling: increase/decrease EC2 instances "desired" count
  - EC2 Actions: stop, terminate, reboot, recover EC2 instance
  - SNS notifications: send notification to SNS topic
- Various options (sampling, %, max, min, etc.)
- Choose period to evaluate alarm
- **Example:** Create billing alarm on CloudWatch Billing metric
- **Alarm States:** OK, INSUFFICIENT_DATA, ALARM

### Amazon CloudWatch Logs
- Collect logs from:
  - Elastic Beanstalk: logs from application
  - ECS: logs from containers
  - AWS Lambda: function logs
  - CloudTrail based on filter
  - CloudWatch log agents: on EC2 machines or on-premises servers
  - Route53: Log DNS queries
- Enables real-time monitoring of logs
- Adjustable CloudWatch Logs retention

### CloudWatch Logs for EC2
- **By default, no logs from EC2 go to CloudWatch**
- Need to run CloudWatch agent on EC2 to push log files
- Make sure IAM permissions are correct
- CloudWatch log agent can be setup on-premises too

### Amazon EventBridge (formerly CloudWatch Events)
- **Schedule:** Cron jobs (scheduled scripts)
- **Event Pattern:** Event rules to react to service doing something
- Trigger Lambda functions, send SQS/SNS messages

### EventBridge Rules
- **Example Sources:**
  - EC2 Instance (e.g., Start Instance)
  - CodeBuild (e.g., failed build)
  - S3 Event (e.g., upload object)
  - Trusted Advisor (e.g., new Finding)
  - CloudTrail (any API call)
  - Schedule or Cron (e.g., every 4 hours)
- **Example Destinations:**
  - Lambda, AWS Batch, ECS Task
  - SQS, SNS, Kinesis Data Streams
  - Step Functions, CodePipeline, CodeBuild
  - SSM, EC2 Actions

### EventBridge Features
- **Schema Registry:** Model event schema
- **Archive events:** Archive events sent to event bus (indefinitely or set period)
- **Replay archived events**
- **Event Buses:**
  - Default Event Bus (AWS Services)
  - Partner Event Bus (AWS SaaS Partners)
  - Custom Event Bus (Custom Apps)

### AWS CloudTrail 📜
- Provides governance, compliance, audit for AWS Account
- **CloudTrail is enabled by default!** ✅
- Get history of events/API calls made within AWS Account by:
  - Console
  - SDK
  - CLI
  - AWS Services
- Can put logs from CloudTrail into CloudWatch Logs or S3
- Trail can be applied to All Regions (default) or single Region
- **If resource deleted in AWS, investigate CloudTrail first!**

### AWS X-Ray
- **Visual analysis of applications**
- Debugging in production for distributed services
- **Advantages:**
  - Troubleshoot performance (bottlenecks)
  - Understand dependencies in microservice architecture
  - Pinpoint service issues
  - Review request behavior
  - Find errors and exceptions
  - Are we meeting time SLA?
  - Where am I throttled?
  - Identify users that are impacted

### Amazon CodeGuru
- ML-powered service for automated code reviews and application performance recommendations
- **Two functionalities:**
  1. **CodeGuru Reviewer:** Automated code reviews for static code analysis (development)
  2. **CodeGuru Profiler:** Visibility/recommendations about application performance during runtime (production)

### CodeGuru Reviewer
- Identify critical issues, security vulnerabilities, hard-to-find bugs
- Uses Machine Learning and automated reasoning
- Supports Java and Python
- Integrates with: GitHub, Bitbucket, AWS CodeCommit

### CodeGuru Profiler
- Understand runtime behavior of application
- **Features:**
  - Identify and remove code inefficiencies
  - Improve application performance (reduce CPU utilization)
  - Decrease compute costs
  - Provides heap summary (identify objects using memory)
  - Anomaly Detection
  - Support applications on AWS or on-premise
  - Minimal overhead on application

### AWS Health Dashboard
- **Service History:**
  - Shows all regions, all services health
  - Shows historical information for each day
  - Has RSS feed
  - Previously called AWS Service Health Dashboard

- **Your Account:**
  - Previously called AWS Personal Health Dashboard (PHD)
  - Provides alerts and remediation guidance when AWS events may impact you
  - Personalized view into performance and availability of AWS services
  - Displays relevant and timely information
  - Can aggregate data from entire AWS Organization
  - **Global service**

### Monitoring Summary 📋
- **CloudWatch:**
  - Metrics: Monitor performance of AWS services and billing metrics
  - Alarms: Automate notification, perform EC2 action, notify to SNS
  - Logs: Collect log files from EC2, servers, Lambda functions
  - Events (EventBridge): React to events in AWS, trigger rule on schedule
- **CloudTrail:** Audit API calls made within AWS account
- **X-Ray:** Trace requests through distributed applications
- **AWS Health Dashboard:** Status of all AWS services across all regions
- **AWS Account Health Dashboard:** AWS events that impact your infrastructure
- **CodeGuru:** Automated code reviews and application performance recommendations

---

<a id="13-amazon-vpc"></a>
## 13. 🔒 Amazon VPC

### VPC Overview 🔒
- **VPC = Virtual Private Cloud**
- Private network to deploy resources (regional resource)
- **At Cloud Practitioner Level:** Know about VPC, Subnets, Internet Gateways, NAT Gateways, Security Groups, NACL, VPC Flow Logs, VPC Peering, VPC Endpoints, Site to Site VPN, Direct Connect, Transit Gateway 📌

### IP Addresses in AWS
- **IPv4:**
  - Public IPv4: Can be used on Internet
  - EC2 gets new public IP every time you stop/start (default)
  - Private IPv4: Used on private networks (e.g., 192.168.1.1)
  - Private IPv4 is fixed for EC2 Instances
  - **Elastic IP:** Fixed public IPv4 address to EC2 instance
  - **Note:** All public IPv4 on AWS charged $0.005 per hour (including EIP)
- **IPv6:**
  - Every IP address is public in AWS (no private range)
  - Example: 2001:db8:3333:4444:cccc:dddd:eeee:ffff
  - **Free**

### VPC & Subnets
- **VPC:** Virtual Private Cloud - private network (regional resource)
- **Subnets:** Partition network inside VPC (Availability Zone resource)
- **Public Subnet:** Accessible from internet
- **Private Subnet:** Not accessible from internet
- **Route Tables:** Define access to internet and between subnets

### Internet Gateway & NAT Gateways
- **Internet Gateway:** Helps VPC instances connect with internet
  - Public Subnets have route to internet gateway
- **NAT Gateways (AWS-managed) & NAT Instances (self-managed):**
  - Allow instances in Private Subnets to access internet while remaining private

### Network ACL & Security Groups
- **NACL (Network ACL):**
  - Firewall controlling traffic from/to subnet
  - Can have ALLOW and DENY rules
  - Attached at Subnet level
  - Rules only include IP addresses
- **Security Groups:**
  - Firewall controlling traffic to/from EC2 Instance
  - Can have only ALLOW rules
  - Rules include IP addresses and other security groups

### VPC Flow Logs
- Capture information about IP traffic going into interfaces:
  - VPC Flow Logs
  - Subnet Flow Logs
  - Elastic Network Interface Flow Logs
- **Helps monitor & troubleshoot connectivity issues**
- Captures network information from AWS managed interfaces: ELB, ElastiCache, RDS, Aurora, etc.
- VPC Flow logs data can go to: S3, CloudWatch Logs, Amazon Data Firehose

### VPC Peering
- Connect two VPC privately using AWS' network
- Make them behave as if in same network
- **Must not have overlapping CIDR** (IP address range)
- **VPC Peering connection is NOT transitive**
  - Must be established for each VPC that needs to communicate

### VPC Endpoints
- Allow connection to AWS Services using private network instead of public www
- Enhanced security and lower latency
- **VPC Endpoint Gateway:** S3 & DynamoDB
- **VPC Endpoint Interface:** Most services (including S3 & DynamoDB)

### AWS PrivateLink (VPC Endpoint Services)
- Most secure & scalable way to expose service to 1000s of VPCs
- Does not require VPC peering, internet gateway, NAT, route tables
- Requires Network Load Balancer (Service VPC) and ENI (Customer VPC)

### Site to Site VPN & Direct Connect
- **Site to Site VPN:**
  - Connect on-premises VPN to AWS
  - Connection automatically encrypted
  - Goes over public internet
  - On-premises: Customer Gateway (CGW)
  - AWS: Virtual Private Gateway (VGW)
- **Direct Connect (DX):**
  - Establish physical connection between on-premises and AWS
  - Connection is private, secure, fast
  - Goes over private network
  - Takes at least a month to establish

### AWS Client VPN
- Connect from computer using OpenVPN to private network in AWS and on-premises
- Connect to EC2 instances over private IP
- Goes over public Internet

### Transit Gateway
- For transitive peering between thousands of VPC and on-premises
- Hub-and-spoke (star) connection
- One single Gateway
- Works with Direct Connect Gateway, VPN connections

### VPC Summary 📋
- **VPC:** Virtual Private Cloud
- **Subnets:** Tied to AZ, network partition of VPC
- **Internet Gateway:** At VPC level, provide Internet Access
- **NAT Gateway/Instances:** Give internet access to private subnets
- **NACL:** Stateless, subnet rules for inbound and outbound
- **Security Groups:** Stateful, operate at EC2 instance level or ENI
- **VPC Peering:** Connect two VPC with non-overlapping IP ranges, non-transitive
- **Elastic IP:** Fixed public IPv4, ongoing cost if not in-use
- **VPC Endpoints:** Provide private access to AWS Services within VPC
- **PrivateLink:** Privately connect to service in 3rd party VPC
- **VPC Flow Logs:** Network traffic logs
- **Site to Site VPN:** VPN over public internet between on-premises DC and AWS
- **Client VPN:** OpenVPN connection from computer into VPC
- **Direct Connect:** Direct private connection to AWS
- **Transit Gateway:** Connect thousands of VPC and on-premises networks together

---

<a id="14-security--compliance"></a>
## 14. 🛡️ Security & Compliance

### AWS Shared Responsibility Model 🤝
- **AWS Responsibility - Security of the Cloud:** ☁️
  - Protecting infrastructure (hardware, software, facilities, networking)
  - Managed services like S3, DynamoDB, RDS, etc.
- **Customer Responsibility - Security in the Cloud:** 👤
  - For EC2: Guest OS management (patches, updates), firewall & network configuration, IAM
  - Encrypting application data
- **Shared Controls:** 🔄
  - Patch Management, Configuration Management, Awareness & Training

### Example: RDS Shared Responsibility
- **AWS Responsible:**
  - Manage underlying EC2 instance, disable SSH access
  - Automated DB patching
  - Automated OS patching
  - Audit underlying instance and disks
- **Your Responsibility:**
  - Check ports/IP/security group inbound rules
  - In-database user creation and permissions
  - Creating database with or without public access
  - Ensure parameter groups/DB configured to only allow SSL connections
  - Database encryption setting

### Example: S3 Shared Responsibility
- **AWS Responsible:**
  - Guarantee unlimited storage
  - Guarantee encryption
  - Ensure separation of data between customers
  - Ensure AWS employees can't access your data
- **Your Responsibility:**
  - Bucket configuration
  - Bucket policy/public setting
  - IAM user and roles
  - Enabling encryption

### DDoS Attack
- **DDoS = Distributed Denial-of-Service**
- Attacker uses bots to overwhelm application server
- Makes application not accessible/not responsive

### DDoS Protection on AWS 🛡️
- **AWS Shield Standard:** 🆓
  - Protects against DDoS for all customers at no additional cost
- **AWS Shield Advanced:** 💎
  - 24/7 premium DDoS protection
- **AWS WAF:** 🔥
  - Filter specific requests based on rules
- **CloudFront and Route 53:** 🌐
  - Availability protection using global edge network
  - Combined with AWS Shield, provides attack mitigation at edge
- **Be ready to scale:** Leverage AWS Auto Scaling 📈

### AWS Shield
- **Standard:**
  - Free service activated for every AWS customer
  - Protection from SYN/UDP Floods, Reflection attacks, layer 3/layer 4 attacks
- **Advanced:**
  - Optional DDoS mitigation service ($3,000 per month per organization)
  - Protect against sophisticated attacks on EC2, ELB, CloudFront, Global Accelerator, Route 53
  - 24/7 access to AWS DDoS response team (DRP)
  - Protect against higher fees during usage spikes due to DDoS

### AWS WAF (Web Application Firewall)
- Protects web applications from common web exploits (Layer 7)
- Layer 7 is HTTP (vs Layer 4 is TCP)
- Deploy on: Application Load Balancer, API Gateway, CloudFront
- **Define Web ACL (Web Access Control List):**
  - Rules can include: IP addresses, HTTP headers, HTTP body, URI strings
  - Protects from: SQL injection, Cross-Site Scripting (XSS)
  - Size constraints, geo-match (block countries)
  - Rate-based rules (count occurrences of events) - for DDoS protection

### AWS Network Firewall
- Protect entire Amazon VPC
- From Layer 3 to Layer 7 protection
- Any direction inspection:
  - VPC to VPC traffic
  - Outbound to internet
  - Inbound from internet
  - To/from Direct Connect & Site-to-Site VPN

### AWS Firewall Manager
- Manage security rules in all accounts of AWS Organization
- Security policy: Common set of security rules
- **Applies to:**
  - VPC Security Groups for EC2, ALB, etc.
  - WAF rules
  - AWS Shield Advanced
  - AWS Network Firewall
- Rules applied to new resources as created (good for compliance) across all and future accounts

### Penetration Testing on AWS
- AWS customers welcome to carry out security assessments or penetration tests **without prior approval** for 8 services:
  - EC2 instances, NAT Gateways, ELB
  - RDS, CloudFront, Aurora
  - API Gateways
  - Lambda and Lambda Edge functions
  - Lightsail resources
  - Elastic Beanstalk environments

### Prohibited Penetration Testing Activities
- DNS zone walking via Route 53 Hosted Zones
- DoS, DDoS, Simulated DoS, Simulated DDoS
- Port flooding, Protocol flooding, Request flooding
- For any other simulated events, contact aws-security-simulated-event@amazon.com

### Data at Rest vs Data in Transit
- **At Rest:** Data stored or archived on device
  - Hard disk, RDS instance, S3 Glacier Deep Archive, etc.
- **In Transit (In Motion):** Data being moved from one location to another
  - Transfer from on-premises to AWS, EC2 to DynamoDB, etc.
- **We want to encrypt data in both states!**

### AWS KMS (Key Management Service) 🔐
- **Anytime you hear "encryption" for AWS service, it's most likely KMS** 💡
- AWS manages encryption keys for us
- **Encryption Opt-in:** ✅
  - EBS volumes: Encrypt volumes
  - S3 buckets: Server-side encryption (SSE-S3 enabled by default, SSE-KMS opt in)
  - Redshift database: Encryption of data
  - RDS database: Encryption of data
  - EFS drives: Encryption of data
- **Encryption Automatically Enabled:**
  - CloudTrail Logs
  - S3 Glacier
  - Storage Gateway

### CloudHSM
- **KMS:** AWS manages software for encryption
- **CloudHSM:** AWS provisions encryption hardware
- Dedicated Hardware (HSM = Hardware Security Module)
- **You manage your own encryption keys entirely (not AWS)**
- HSM device is tamper resistant, FIPS 140-2 Level 3 compliance

### Types of KMS Keys
1. **Customer Managed Key:**
   - Create, manage, used by customer
   - Can enable/disable
   - Possibility of rotation policy (new key every year, old key preserved)
   - Possibility to bring-your-own-key

2. **AWS Managed Key:**
   - Created, managed, used on customer's behalf by AWS
   - Used by AWS services (aws/s3, aws/ebs, aws/redshift)

3. **AWS Owned Key:**
   - Collection of CMKs that AWS service owns and manages
   - AWS can use to protect resources in your account (can't view keys)

4. **CloudHSM Keys (custom keystore):**
   - Keys generated from your own CloudHSM hardware device
   - Cryptographic operations performed within CloudHSM cluster

### AWS Certificate Manager (ACM)
- Easily provision, manage, deploy SSL/TLS Certificates
- Used to provide in-flight encryption for websites (HTTPS)
- Supports both public and private TLS certificates
- **Free of charge for public TLS certificates**
- Automatic TLS certificate renewal
- **Integrations:**
  - Elastic Load Balancers
  - CloudFront Distributions
  - APIs on API Gateway

### AWS Secrets Manager
- Newer service for storing secrets
- Capability to force rotation of secrets every X days
- Automate generation of secrets on rotation (uses Lambda)
- Integration with Amazon RDS (MySQL, PostgreSQL, Aurora)
- Secrets encrypted using KMS
- Mostly meant for RDS integration

### AWS Artifact
- Portal providing on-demand access to AWS compliance documentation and AWS agreements
- **Artifact Reports:**
  - Download AWS security and compliance documents from third-party auditors
  - AWS ISO certifications, PCI, SOC reports
- **Artifact Agreements:**
  - Review, accept, track status of AWS agreements
  - BAA (Business Associate Addendum), HIPAA
  - For individual account or organization
- Can be used to support internal audit or compliance

### Amazon GuardDuty
- Intelligent Threat discovery to protect AWS Account
- Uses Machine Learning algorithms, anomaly detection, 3rd party data
- **One click to enable (30 days trial)**, no need to install software
- **Input data includes:**
  - CloudTrail Events Logs: Unusual API calls, unauthorized deployments
  - CloudTrail Management Events: Create VPC subnet, create trail, etc.
  - CloudTrail S3 Data Events: Get object, list objects, delete object, etc.
  - VPC Flow Logs: Unusual internal traffic, unusual IP address
  - DNS Logs: Compromised EC2 instances sending encoded data within DNS queries
- **Optional Features:** EKS Audit Logs, RDS & Aurora, EBS, Lambda, S3 Data Events
- Can setup EventBridge rules to be notified in case of findings
- Can protect against CryptoCurrency attacks

### Amazon Inspector
- Automated Security Assessments
- **For EC2 instances:**
  - Leveraging SSM agent
  - Analyze against unintended network accessibility
  - Analyze running OS against known vulnerabilities
- **For Container Images (ECR):**
  - Assessment of Container Images as pushed
- **For Lambda Functions:**
  - Identifies software vulnerabilities in function code and package dependencies
  - Assessment of functions as deployed
- Reporting & integration with AWS Security Hub
- Send findings to Amazon EventBridge

### What Inspector Evaluates
- **Only for EC2 instances, Container Images & Lambda functions**
- Continuous scanning of infrastructure, only when needed
- Package vulnerabilities (EC2, ECR & Lambda) - database of CVE
- Network reachability (EC2)
- Risk score associated with all vulnerabilities for prioritization

### AWS Config
- Helps with auditing and recording compliance of AWS resources
- Records configurations and changes over time
- Possibility of storing configuration data into S3 (analyzed by Athena)
- **Questions solved by AWS Config:**
  - Is there unrestricted SSH access to my security groups?
  - Do my buckets have any public access?
  - How has my ALB configuration changed over time?
- Can receive alerts (SNS notifications) for any changes
- **AWS Config is a per-region service**
- Can be aggregated across regions and accounts

### AWS Macie
- Fully managed data security and data privacy service
- Uses machine learning and pattern matching
- Discover and protect sensitive data in AWS
- Helps identify and alert to sensitive data, such as PII (Personally Identifiable Information)
- Primarily for S3 Buckets

### AWS Security Hub
- Central security tool to manage security across several AWS accounts
- Automate security checks
- Integrated dashboards showing current security and compliance status
- Automatically aggregates alerts from:
  - Config, GuardDuty, Inspector, Macie
  - IAM Access Analyzer
  - Systems Manager, Firewall Manager
  - AWS Health
  - AWS Partner Network Solutions
- **Must first enable AWS Config Service**

### Amazon Detective
- GuardDuty, Macie, Security Hub identify potential security issues
- Sometimes security findings require deeper analysis to isolate root cause
- Amazon Detective analyzes, investigates, identifies root cause (using ML and graphs)
- Automatically collects and processes events from:
  - VPC Flow Logs, CloudTrail, GuardDuty
- Creates unified view
- Produces visualizations with details and context

### AWS Abuse
- Report suspected AWS resources used for abusive or illegal purposes
- **Abusive & prohibited behaviors:**
  - Spam
  - Port scanning
  - DoS or DDoS attacks
  - Intrusion attempts
  - Hosting objectionable or copyrighted content
  - Distributing malware
- Contact: AWS abuse form or abuse@amazonaws.com

### Root User Privileges
- **Root user = Account Owner** (created when account is created)
- Has complete access to all AWS services and resources
- **Lock away AWS account root user access keys!**
- Do not use root account for everyday tasks
- **Actions that can be performed only by root user:**
  - Change account settings (account name, email, root password, root access keys)
  - View certain tax invoices
  - Close AWS account
  - Restore IAM user permissions
  - Change or cancel AWS Support plan
  - Register as seller in Reserved Instance Marketplace
  - Configure S3 bucket to enable MFA
  - Edit or delete S3 bucket policy with invalid VPC ID or VPC endpoint ID
  - Sign up for GovCloud

### IAM Access Analyzer
- Find out which resources are shared externally
- **Resources analyzed:**
  - S3 Buckets
  - IAM Roles
  - KMS Keys
  - Lambda Functions and Layers
  - SQS queues
  - Secrets Manager Secrets
- **Define Zone of Trust = AWS Account or AWS Organization**
- Access outside zone of trusts => findings

### Security & Compliance Summary 📋
- **Shared Responsibility Model:** AWS = Security of Cloud, Customer = Security in Cloud
- **Shield:** Automatic DDoS Protection + 24/7 support for advanced
- **WAF:** Firewall to filter incoming requests based on rules
- **KMS:** Encryption keys managed by AWS
- **CloudHSM:** Hardware encryption, we manage encryption keys
- **ACM:** Provision, manage, deploy SSL/TLS Certificates
- **Artifact:** Get access to compliance reports (PCI, ISO, etc.)
- **GuardDuty:** Find malicious behavior with VPC, DNS & CloudTrail Logs
- **Inspector:** Find software vulnerabilities in EC2, ECR Images, Lambda functions
- **Network Firewall:** Protect VPC against network attacks
- **Config:** Track config changes and compliance against rules
- **Macie:** Find sensitive data (PII) in S3 buckets
- **CloudTrail:** Track API calls made by users within account
- **Security Hub:** Gather security findings from multiple AWS accounts
- **Detective:** Find root cause of security issues or suspicious activities
- **AWS Abuse:** Report AWS resources used for abusive or illegal purposes
- **IAM Access Analyzer:** Identify which resources are shared externally
- **Firewall Manager:** Manage security rules across Organization (WAF, Shield...)

---

<a id="15-machine-learning"></a>
## 15. 🤖 Machine Learning

### Amazon Rekognition 👁️
- Find objects, people, text, scenes in images and videos using ML
- Facial analysis and facial search for user verification, people counting
- Create database of "familiar faces" or compare against celebrities
- **Use cases:** 📌
  - Labeling
  - Content Moderation
  - Text Detection
  - Face Detection and Analysis (gender, age range, emotions...)
  - Face Search and Verification
  - Celebrity Recognition
  - Pathing (e.g., for sports game analysis)

### Amazon Transcribe
- Automatically convert speech to text
- Uses deep learning process called automatic speech recognition (ASR)
- Automatically remove PII using Redaction
- Supports Automatic Language Identification for multi-lingual audio
- **Use cases:**
  - Transcribe customer service calls
  - Automate closed captioning and subtitling
  - Generate metadata for media assets to create searchable archive

### Amazon Polly
- Turn text into lifelike speech using deep learning
- Allows you to create applications that talk

### Amazon Translate
- Natural and accurate language translation
- Localize content (websites, applications) for international users
- Translate large volumes of text efficiently

### Amazon Lex & Connect
- **Amazon Lex:** (Same technology that powers Alexa)
  - Automatic Speech Recognition (ASR) to convert speech to text
  - Natural Language Understanding to recognize intent of text, callers
  - Helps build chatbots, call center bots
- **Amazon Connect:**
  - Receive calls, create contact flows
  - Cloud-based virtual contact center
  - Can integrate with other CRM systems or AWS
  - No upfront payments, 80% cheaper than traditional contact center solutions

### Amazon Comprehend
- Natural Language Processing (NLP)
- Fully managed and serverless service
- Uses machine learning to find insights and relationships in text
- **Features:**
  - Language of the text
  - Extracts key phrases, places, people, brands, events
  - Understands how positive or negative text is
  - Analyzes text using tokenization and parts of speech
  - Automatically organizes collection of text files by topic
- **Use cases:**
  - Analyze customer interactions (emails) to find positive/negative experience
  - Create and group articles by topics

### Amazon SageMaker
- Fully managed service for developers/data scientists to build ML models
- Typically difficult to do all processes in one place + provision servers
- **Machine Learning Process:**
  1. Historical Data (features)
  2. Build ML model
  3. Train and Tune
  4. Apply model to new data
  5. Prediction

### Amazon Kendra
- Fully managed document search service powered by Machine Learning
- Extract answers from within documents (text, pdf, HTML, PowerPoint, MS Word, FAQs...)
- Natural language search capabilities
- Learn from user interactions/feedback to promote preferred results (Incremental Learning)
- Ability to manually fine-tune search results
- **Data Sources:** S3, RDS, Google Drive, MS SharePoint, MS OneDrive, 3rd party, APIs, Custom

### Amazon Personalize
- Fully managed ML-service to build apps with real-time personalized recommendations
- **Example:** Personalized product recommendations/re-ranking, customized direct marketing
- Same technology used by Amazon.com
- Integrates into existing websites, applications, SMS, email marketing systems
- Implement in days, not months
- **Use cases:** Retail stores, media and entertainment

### Amazon Textract
- Automatically extracts text, handwriting, and data from scanned documents using AI and ML
- Extract data from forms and tables
- Read and process any type of document (PDFs, images...)
- **Use cases:**
  - Financial Services (invoices, financial reports)
  - Healthcare (medical records, insurance claims)
  - Public Sector (tax forms, ID documents, passports)

### AWS Machine Learning Summary 📋
- **Rekognition:** Face detection, labeling, celebrity recognition
- **Transcribe:** Audio to text (subtitles)
- **Polly:** Text to audio
- **Translate:** Translations
- **Lex:** Build conversational bots - chatbots
- **Connect:** Cloud contact center
- **Comprehend:** Natural language processing
- **SageMaker:** Machine learning for every developer and data scientist
- **Kendra:** ML-powered search engine
- **Personalize:** Real-time personalized recommendations
- **Textract:** Detect text and data in documents

---

<a id="16-account-management-billing--support"></a>
## 16. 💳 Account Management, Billing, & Support

### AWS Organizations 🏢
- **Global service**
- Allows managing multiple AWS accounts
- Main account is the **master account**
- **Cost Benefits:** 💰
  - Consolidated Billing across all accounts - single payment method
  - Pricing benefits from aggregated usage (volume discount for EC2, S3...)
  - Pooling of Reserved EC2 instances for optimal savings
- API available to automate AWS account creation
- Restrict account privileges using Service Control Policies (SCP)

### Multi Account Strategies
- Create accounts per:
  - Department
  - Cost center
  - Dev / Test / Prod
  - Regulatory restrictions (using SCP)
  - Better resource isolation (e.g., VPC)
  - Separate per-account service limits
  - Isolated account for logging
- **Multi Account vs One Account Multi VPC**
- Use tagging standards for billing purposes
- Enable CloudTrail on all accounts, send logs to central S3 account
- Send CloudWatch Logs to central logging account

### Organizational Units (OU)
- Examples:
  - Business Unit
  - Environmental (Lifecycle)
  - Project-based

### Service Control Policies (SCP)
- Whitelist or blacklist IAM actions
- Applied at OU or Account level
- **Does not apply to Master Account**
- SCP applied to all Users and Roles of Account, including Root user
- SCP does not affect service-linked roles
- **SCP must have explicit Allow** (does not allow anything by default)
- **Use cases:**
  - Restrict access to certain services (e.g., can't use EMR)
  - Enforce PCI compliance by explicitly disabling services

### AWS Organization - Consolidated Billing
- **When enabled:**
  - **Combined Usage:** Combine usage across all accounts to share volume pricing, Reserved Instances, Savings Plans discounts
  - **One Bill:** Get one bill for all AWS Accounts
  - Management account can turn off Reserved Instances discount sharing for any account

### AWS Control Tower
- Easy way to set up and govern secure and compliant multi-account AWS environment based on best practices
- **Benefits:**
  - Automate set up of environment in few clicks
  - Automate ongoing policy management using guardrails
  - Detect policy violations and remediate them
  - Monitor compliance through interactive dashboard
- **Runs on top of AWS Organizations:**
  - Automatically sets up AWS Organizations
  - Organize accounts and implement SCPs

### AWS Resource Access Manager (RAM)
- Share AWS resources that you own with other AWS accounts
- Share with any account or within Organization
- **Avoid resource duplication!**
- **Supported resources:**
  - Aurora, VPC Subnets, Transit Gateway, Route 53
  - EC2 Dedicated Hosts, License Manager Configurations...

### AWS Service Catalog
- Users new to AWS have too many options
- May create stacks not compliant/in line with organization
- Some users want quick self-service portal to launch authorized products pre-defined by admins
- Includes: virtual machines, databases, storage options, etc.

### Service Catalog Diagram
- **Admin Tasks:**
  - Product (CloudFormation Templates)
  - Portfolio (Collection of Products)
  - IAM Permissions to Access Portfolios
- **User Tasks:**
  - Product List (Authorized by IAM)
  - Launch
  - Provisioned Products (Ready to use, Properly Configured, Properly Tagged)

### Pricing Models in AWS
1. **Pay as you go:**
   - Pay for what you use
   - Remain agile, responsive, meet scale demands

2. **Save when you reserve:**
   - Minimize risks, predictably manage budgets
   - Comply with long-term requirements
   - Reservations available for: EC2 Reserved Instances, DynamoDB Reserved Capacity, ElastiCache Reserved Nodes, RDS Reserved Instance, Redshift Reserved Nodes

3. **Pay less by using more:**
   - Volume-based discounts

4. **Pay less as AWS grows:**
   - Prices reduced as AWS becomes more efficient

### Free Services & Free Plan in AWS
- With new AWS account, get up to **$200 in credits**
- Choose between **Free Plan or Paid Plan**
- **Free Plan:** Expires in 6 months or when credits consumed (no charges)
- **Paid Plan:** Charged after consuming credits
- **Both Plans have access to Always Free Services**
- **Monthly free usage limits examples:**
  - Lambda: 1,000,000 requests/month and 400,000 GB-seconds compute/month
  - DynamoDB: 25 GB storage and 200M requests/month

### Compute Pricing - EC2
- **Charged for:**
  - Number of instances
  - Instance configuration (physical capacity, region, OS, software, instance type, size)
  - ELB running time and data processed
  - Detailed monitoring
- **On-demand instances:**
  - Minimum of 60s
  - Pay per second (Linux/Windows) or per hour (other)
- **Reserved instances:**
  - Up to 75% discount vs On-demand
  - 1- or 3-years commitment
  - All upfront, partial upfront, no upfront
- **Spot instances:**
  - Up to 90% discount vs On-demand
  - Bid for unused capacity
- **Dedicated Host:**
  - On-demand
  - Reservation for 1 year or 3 years
- **Savings Plans:** Alternative to save on sustained usage

### Compute Pricing - Lambda & ECS
- **Lambda:**
  - Pay per call
  - Pay per duration
- **ECS:**
  - **EC2 Launch Type:** No additional fees, pay for AWS resources
  - **Fargate Launch Type:** Pay for vCPU and memory resources allocated to containers

### Storage Pricing - S3
- Storage class (Standard, IA, One-Zone IA, Intelligent Tiering, Glacier, Deep Archive)
- Number and size of objects (tiered pricing based on volume)
- Number and type of requests
- Data transfer OUT of S3 region
- S3 Transfer Acceleration
- Lifecycle transitions
- **Similar service:** EFS (pay per use, has infrequent access & lifecycle rules)

### Storage Pricing - EBS
- Volume type (based on performance)
- Storage volume in GB per month provisioned
- **IOPS:**
  - General Purpose SSD: Included
  - Provisioned IOPS SSD: Provisioned amount in IOPS
  - Magnetic: Number of requests
- **Snapshots:** Added data cost per GB per month
- **Data transfer:**
  - Outbound data transfer tiered for volume discounts
  - Inbound is free

### Database Pricing - RDS
- Per hour billing
- **Database characteristics:**
  - Engine, Size, Memory class
- **Purchase type:**
  - On-demand
  - Reserved instances (1 or 3 years) with optional upfront
- **Backup Storage:**
  - No additional charge for backup storage up to 100% of total database storage for region
- Additional storage (per GB per month)
- Number of input and output requests per month
- **Deployment type:**
  - Single AZ
  - Multiple AZs (storage and I/O are variable)
- **Data transfer:**
  - Outbound tiered for volume discounts
  - Inbound is free

### Content Delivery - CloudFront
- Pricing different across geographic regions
- Aggregated for each edge location, then applied to bill
- Data Transfer Out (volume discount)
- Number of HTTP/HTTPS requests

### Networking Costs in AWS per GB
- **Same AZ:** Free if using private IP, $0.02 if using Public IP/Elastic IP
- **Different AZ, Same Region:** $0.01 if using private IP
- **Inter-region:** $0.02
- **Use Private IP instead of Public IP** for good savings and better network performance
- **Use same AZ** for maximum savings (at cost of high availability)
- **Free for traffic in**

### Savings Plan
- Commit certain $ amount per hour for 1 or 3 years
- Easiest way to setup long-term commitments on AWS
- **EC2 Savings Plan:**
  - Up to 72% discount vs On-Demand
  - Commit to usage of individual instance families in region (e.g., C5 or M5)
  - Regardless of AZ, size, OS, tenancy
  - All upfront, partial upfront, no upfront
- **Compute Savings Plan:**
  - Up to 66% discount vs On-Demand
  - Regardless of Family, Region, size, OS, tenancy, compute options
  - Compute Options: EC2, Fargate, Lambda
- **Machine Learning Savings Plan:** SageMaker...
- Setup from AWS Cost Explorer console

### AWS Compute Optimizer
- Reduce costs and improve performance by recommending optimal AWS resources
- Helps choose optimal configurations and right-size workloads (over/under provisioned)
- Uses Machine Learning to analyze resources' configurations and CloudWatch metrics
- **Supported resources:**
  - EC2 instances
  - EC2 Auto Scaling Groups
  - EBS volumes
  - Lambda functions
- Lower costs by up to 25%
- Recommendations can be exported to S3

### Billing and Costing Tools
- **Estimating costs:**
  - Pricing Calculator
- **Tracking costs:**
  - Billing Dashboard
  - Cost Allocation Tags
  - Cost and Usage Reports
  - Cost Explorer
- **Monitoring against cost plans:**
  - Billing Alarms
  - Budgets

### AWS Pricing Calculator
- Available at https://calculator.aws/
- Estimate cost for solution architecture

### AWS Billing Dashboard
- View billing information and invoices

### Cost Allocation Tags
- Track AWS costs on detailed level
- **AWS generated tags:**
  - Automatically applied to resources
  - Starts with prefix `aws:` (e.g., aws:createdBy)
- **User-defined tags:**
  - Defined by user
  - Starts with prefix `user:`

### Tagging and Resource Groups
- Tags used for organizing resources:
  - EC2: instances, images, load balancers, security groups...
  - RDS, VPC resources, Route 53, IAM users, etc.
- Resources created by CloudFormation are all tagged same way
- Common tags: Name, Environment, Team...
- Tags can be used to create Resource Groups
- Manage tags using Tag Editor

### Cost and Usage Reports
- Most comprehensive set of AWS cost and usage data
- Includes metadata about AWS services, pricing, reservations
- Lists AWS usage for each service category in hourly or daily line items
- Includes tags activated for cost allocation
- Can be integrated with Athena, Redshift, QuickSight

### Cost Explorer
- Visualize, understand, manage AWS costs and usage over time
- Create custom reports analyzing cost and usage data
- Analyze data at high level: total costs and usage across all accounts
- Or Monthly, hourly, resource level granularity
- Choose optimal Savings Plan
- Forecast usage up to 12 months based on previous usage

### AWS Budgets
- Set custom budgets to track cost and usage
- Get alerts when cost or usage exceeds (or forecasted to exceed) budgeted amount
- **3 types of budgets:**
  1. Cost budgets: Plan how much you want to spend on service
  2. Usage budgets: Plan how much you want to use one or more services
  3. Reservation budgets: Track utilization of Reserved Instances or Savings Plans
- **Budget actions:**
  - Trigger when threshold exceeded
  - Can trigger SNS notifications
  - Can apply IAM actions

### AWS Support Plans 📞
1. **Basic Support:** 🆓
   - Free
   - 24/7 customer service
   - Documentation, whitepapers, support forums
   - AWS Personal Health Dashboard
   - Service health checks

2. **Developer Support:** 👨‍💻
   - $29/month or 3% of monthly AWS usage
   - Business hours email access to Cloud Support Associates
   - 1 business day response time
   - Client-side diagnostic tools
   - Building-block architecture support

3. **Business Support:** 💼
   - $100/month or 10% of monthly AWS usage (up to $10,000)
   - 24/7 email, chat, phone access to Cloud Support Engineers
   - 1 hour response time for production system down
   - 4 hours for production system impaired
   - Infrastructure event management
   - AWS Trusted Advisor
   - AWS Support API

4. **Enterprise Support:** 🏆
   - $15,000/month or 10% of monthly AWS usage (up to $150,000)
   - 24/7 email, chat, phone access to Cloud Support Engineers
   - 15 minute response time for business-critical system down
   - 1 hour for production system impaired
   - Infrastructure event management
   - AWS Trusted Advisor
   - AWS Support API
   - Technical Account Manager (TAM)
   - Concierge Support Team (billing and account best practices)

### AWS Trusted Advisor 💡
- Online resource to help you reduce cost, increase performance, and improve security
- **Core checks and recommendations (all customers):** ✅
  - Service limits
  - Security groups - specific ports unrestricted
  - IAM use
  - MFA on root account
  - EBS public snapshots
  - RDS public snapshots
- **Full Trusted Advisor (Business & Enterprise Support):**
  - Cost optimization
  - Performance
  - Security
  - Fault tolerance
  - Service limits

### Account Management, Billing & Support Summary 📋
- **AWS Organizations:** Manage multiple AWS accounts, consolidated billing
- **Service Control Policies:** Whitelist/blacklist IAM actions
- **Control Tower:** Set up and govern multi-account environment
- **Resource Access Manager:** Share AWS resources with other accounts
- **Service Catalog:** Self-service portal for authorized products
- **Pricing Models:** Pay as you go, Save when you reserve, Pay less by using more, Pay less as AWS grows
- **Free Tier:** $200 credits, Always Free Services 🎁
- **Pricing:** Varies by service (compute, storage, database, networking)
- **Savings Plans:** Commit $ amount per hour for 1 or 3 years
- **Compute Optimizer:** ML-powered recommendations for optimal resources
- **Billing Tools:** Pricing Calculator, Billing Dashboard, Cost Allocation Tags, Cost and Usage Reports, Cost Explorer, Budgets
- **Support Plans:** Basic (free), Developer, Business, Enterprise
- **Trusted Advisor:** Reduce cost, increase performance, improve security

---

<a id="17-advanced-identity"></a>
## 17. 👤 Advanced Identity

### AWS Single Sign-On (SSO) 🔑
- Centrally manage SSO access to multiple AWS accounts and business applications
- Integrated with AWS Organizations
- Supports SAML 2.0
- Centralized permission management
- Access to AWS accounts or cloud applications
- Integrated with many identity providers (IdP)

### AWS Directory Services
- **AWS Managed Microsoft AD:**
  - Create your own AD in AWS, manage users locally
  - Supports MFA
  - Establish "trust" connections with your on-premises AD
- **AD Connector:**
  - Directory gateway (proxy) to redirect to on-premises AD
  - Users are managed on the on-premises Active Directory
- **Simple AD:**
  - AD-compatible managed directory on AWS
  - Cannot be joined with on-premises AD
  - Use if you don't need advanced AD features

### AWS Cognito
- **User Pools:**
  - Sign in functionality for app users
  - Integrate with API Gateway & Application Load Balancer
- **Identity Pools:**
  - Provide AWS credentials to users so they can access AWS resources directly
  - Integrate with Cognito User Pools as an identity provider

### Advanced Identity Summary 📋
- **AWS SSO:** Centrally manage SSO access to multiple AWS accounts
- **Directory Services:** AWS Managed Microsoft AD, AD Connector, Simple AD
- **Cognito:** User Pools (sign in), Identity Pools (AWS credentials)

---

<a id="18-other-aws-services"></a>
## 18. 📦 Other AWS Services

### AWS Well-Architected Framework 🏗️
- Helps understand pros and cons of decisions you make while building systems on AWS
- **5 Pillars:** 📌
  1. **Operational Excellence** ⚙️
  2. **Security** 🛡️
  3. **Reliability** 🔄
  4. **Performance Efficiency** ⚡
  5. **Cost Optimization** 💰

### AWS Well-Architected Tool
- Free tool to review architectures
- Compare against best practices
- Get advice on how to improve architectures

### AWS Marketplace
- Digital catalog with thousands of software listings from independent software vendors
- Find, test, buy, and deploy software that runs on AWS
- Categories: Infrastructure Software, Business Software, Data Products, DevOps
- Can be free, BYOL (Bring Your Own License), or paid (hourly/monthly)

### AWS DataSync
- Move large amounts of data from on-premises to AWS
- Can synchronize to: S3 (any storage classes), EFS, FSx for Windows
- Replication tasks can be scheduled
- **Use cases:**
  - Migration to AWS
  - Archive to S3
  - Disaster Recovery
  - Data processing workflows

### AWS Application Discovery Service
- Plan migration projects by gathering information about on-premises data centers
- **Agentless Discovery (AWS Agentless Discovery Connector):**
  - VM inventory, configuration, and performance history such as CPU, memory, and disk usage
- **Agent-based Discovery (AWS Application Discovery Agent):**
  - System configuration, system performance, running processes, and details of the network connections between systems
- Resulting data can be viewed within AWS Migration Hub

### AWS Migration Hub
- Provides a single place to discover your existing servers and track migrations
- View migration progress across multiple AWS and partner solutions
- **Works with:**
  - Application Discovery Service
  - Database Migration Service (DMS)
  - Server Migration Service (SMS)
  - AWS and partner migration tools

### AWS Application Migration Service (MGN)
- Lift-and-shift (rehost) solution which simplifies, expedites, and reduces the cost of migrating applications to AWS
- Converts your physical, virtual, or cloud servers to run natively on AWS
- Minimal downtime, reduced costs

### Other AWS Services Summary 📋
- **Well-Architected Framework:** 5 pillars (Operational Excellence, Security, Reliability, Performance Efficiency, Cost Optimization)
- **Marketplace:** Digital catalog of software listings
- **DataSync:** Move large amounts of data from on-premises to AWS
- **Application Discovery Service:** Gather information about on-premises data centers
- **Migration Hub:** Single place to discover servers and track migrations
- **Application Migration Service:** Lift-and-shift solution for migrating applications

---

<a id="19-aws-architecting--ecosystem"></a>
## 19. 🏗️ AWS Architecting & Ecosystem

### AWS Well-Architected Framework Pillars 🏛️

#### 1. Operational Excellence ⚙️
- Run and monitor systems
- Automate changes
- Respond to events
- Evolve procedures

#### 2. Security 🛡️
- Protect information, systems, and assets
- Identity and access management
- Detective controls
- Infrastructure protection
- Data protection

#### 3. Reliability 🔄
- Recover from failures
- Dynamically acquire computing resources
- Mitigate disruptions

#### 4. Performance Efficiency ⚡
- Use computing resources efficiently
- Maintain efficiency as demand changes
- Use technologies appropriately

#### 5. Cost Optimization 💰
- Avoid unnecessary costs
- Understand and control where money is being spent
- Select the right resource types and quantities
- Scale to meet business needs without overspending

### AWS Partner Network (APN)
- Global partner program
- **Technology Partners:**
  - Software: Provide software solutions that run on or integrate with AWS
  - Hardware: Provide hardware solutions that integrate with AWS
  - Training: Provide training and certification
- **Consulting Partners:**
  - Professional services firms that help customers design, architect, build, migrate, and manage their workloads and applications on AWS

### AWS Marketplace
- Digital catalog with thousands of software listings
- Find, test, buy, deploy software that runs on AWS
- Categories: Infrastructure Software, Business Software, Data Products, DevOps

### AWS Architecting & Ecosystem Summary 📋
- **Well-Architected Framework:** 5 pillars for building systems on AWS
- **Well-Architected Tool:** Free tool to review architectures
- **APN:** Global partner program (Technology Partners, Consulting Partners)
- **Marketplace:** Digital catalog of software listings

---

<a id="20-exam-preparation-tips"></a>
## 20. 📝 Exam Preparation Tips

### Exam Overview 📋
- **Exam Code:** CLF-C02
- **Duration:** 90 minutes ⏱️
- **Question Format:** Multiple choice, multiple response
- **Passing Score:** 700/1000 (70%) ✅
- **Cost:** $100 USD 💵

### Key Topics to Focus On 🎯
1. **Cloud Computing Fundamentals** ☁️
   - Characteristics, advantages, deployment models
   - IaaS, PaaS, SaaS

2. **AWS Global Infrastructure** 🌍
   - Regions, Availability Zones, Edge Locations
   - How to choose a region

3. **Core AWS Services** 🛠️
   - EC2, S3, RDS, Lambda, IAM
   - Know use cases, pricing models, features

4. **Security & Compliance** 🛡️
   - Shared Responsibility Model
   - IAM, KMS, Shield, WAF
   - Security best practices

5. **Billing & Pricing** 💳
   - Pricing models (On-Demand, Reserved, Spot)
   - Cost optimization tools
   - Free Tier

6. **Support Plans** 📞
   - Basic, Developer, Business, Enterprise
   - What's included in each

### Study Tips 📚
1. **Understand, Don't Memorize:** 🧠
   - Focus on understanding concepts rather than memorizing facts
   - Know why services exist and when to use them

2. **Practice Questions:** ✏️
   - Use AWS official practice question sets
   - Take practice exams
   - Review incorrect answers

3. **Hands-On Practice:** 🖱️
   - Use AWS Free Tier to practice
   - Create resources in console
   - Understand how services work together

4. **Focus on High-Level:** 📖
   - This is a foundational exam
   - Don't need deep technical details
   - Focus on service purposes and use cases

5. **Review Service Summaries:** 📋
   - Each section has a summary
   - Review these frequently
   - Know key differences between similar services

### Common Exam Topics
- **Service Selection:** Which service to use for a given scenario
- **Pricing:** Understanding cost implications
- **Security:** Best practices, shared responsibility
- **Global Infrastructure:** Regions, AZs, Edge Locations
- **Storage Classes:** S3 storage classes and when to use each
- **Database Types:** When to use RDS vs DynamoDB vs Redshift
- **Compute Options:** EC2 vs Lambda vs Containers
- **Networking:** VPC basics, security groups, NACLs
- **Monitoring:** CloudWatch, CloudTrail
- **Support:** Support plan features

### Exam Day Tips 📅
1. **Read Questions Carefully:** 👀
   - Look for keywords like "most cost-effective", "most secure", "serverless"
   - Eliminate obviously wrong answers first

2. **Time Management:** ⏱️
   - 90 minutes for ~65 questions
   - About 1.4 minutes per question
   - Don't spend too long on one question

3. **Process of Elimination:** ✅
   - Eliminate wrong answers
   - Choose best answer from remaining options

4. **Flag for Review:** 🚩
   - Flag questions you're unsure about
   - Review flagged questions at the end

5. **Stay Calm:** 😌
   - Take deep breaths
   - Read each question carefully
   - Trust your preparation

### Resources 📚
- **AWS Official:** ☁️
  - AWS Certified Cloud Practitioner Exam Guide
  - AWS Training and Certification
  - AWS Whitepapers
  - AWS Well-Architected Framework

- **Practice Exams:** ✏️
  - AWS Official Practice Question Sets
  - Third-party practice exams

- **Documentation:** 📖
  - AWS Service Documentation
  - AWS FAQs

### Final Notes
- This exam tests your understanding of AWS Cloud fundamentals
- Focus on high-level concepts, not deep technical details
- Understand when to use which service
- Know pricing models and cost optimization
- Understand security and compliance basics
- Practice with hands-on labs
- Take practice exams
- Review service summaries frequently

**Good luck with your exam!** 🍀

---

## Additional Resources 📎

### Important URLs 🔗
- AWS Free Tier: https://aws.amazon.com/free/
- AWS Pricing Calculator: https://calculator.aws/
- AWS Global Infrastructure: https://infrastructure.aws/
- AWS Well-Architected: https://aws.amazon.com/architecture/well-architected/
- AWS Training: https://aws.amazon.com/training/

### Key Service Documentation 📖
- **IAM:** https://aws.amazon.com/iam/ 🔐
- **EC2:** https://aws.amazon.com/ec2/ 🖥️
- **S3:** https://aws.amazon.com/s3/ 🪣
- **RDS:** https://aws.amazon.com/rds/ 🗄️
- **Lambda:** https://aws.amazon.com/lambda/ λ
- **CloudWatch:** https://aws.amazon.com/cloudwatch/ 📊
- **CloudTrail:** https://aws.amazon.com/cloudtrail/ 📜

---

**End of Study Notes** ✅


