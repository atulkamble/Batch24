# AWS Notes

## 1. Introduction to AWS and Cloud Computing

Definitions

- Cloud Computing: Delivery of computing resources such as servers, storage, databases and networking over the internet on demand.
- AWS: Amazon Web Services, a cloud computing platform.
- EC2: Elastic Compute Cloud, a service that provides virtual servers.
- Region: A separate geographical area where AWS operates infrastructure.
- Availability Zone (AZ): An isolated location within an AWS Region, comprising one or more data centers.
- IaaS: Infrastructure as a Service, providing virtualized infrastructure.
- PaaS: Platform as a Service, providing a managed platform for applications.
- SaaS: Software as a Service, delivering ready-to-use applications.

Points to remember

- AWS follows a pay-as-you-go pricing model for many services.
- Regions contain multiple Availability Zones.
- EC2 is primarily an IaaS service.
- Windows EC2 commonly uses RDP on port 3389.
- Linux EC2 commonly uses SSH on port 22.
- IIS is Microsoft's web server.
- HTTP uses port 80 and HTTPS uses port 443.
- A public IP can be used to access an internet-facing website when routing and security permit.

## 2. EC2 Linux, Windows and AMI

Definitions

- EC2 Instance: A virtual machine running in AWS.
- AMI: Amazon Machine Image, a template used to launch EC2 instances.
- Instance Type: Determines an EC2 instance's CPU, memory and other resource characteristics.
- Key Pair: Public/private cryptographic keys used for authentication.
- Elastic IP: A static public IPv4 address allocated to an AWS account.
- PuTTY: An SSH client commonly used to connect to Linux servers.

Points to remember

- Linux SSH port: 22.
- Windows RDP port: 3389.
- Apache and Nginx are commonly used Linux web servers.
- AMIs can be copied between AWS Regions.
- AMIs can be shared with specific AWS accounts.
- EBS-backed EC2 instances generally need to be stopped before changing instance type.
- Stopping and starting an instance can change its automatically assigned public IPv4 address.
- AMIs are regional resources.

## 3. Elastic Load Balancing (ELB)

Definitions

- Load Balancer: Distributes incoming traffic across multiple targets.
- ALB: Application Load Balancer, operating at OSI Layer 7.
- NLB: Network Load Balancer, operating at OSI Layer 4.
- GWLB: Gateway Load Balancer, used to deploy and scale network appliances.
- Target Group: A collection of targets that receive traffic.
- Listener: Checks incoming connections on a configured protocol and port.
- Health Check: Determines whether a target is healthy enough to receive traffic.

Points to remember

- ALB supports HTTP and HTTPS traffic.
- NLB supports TCP, UDP and TLS traffic, among other configurations.
- ALB supports path-based and host-based routing.
- Load balancers provide DNS names.
- Only healthy targets normally receive traffic when healthy targets are available.
- An ALB can route traffic to EC2 instances through target groups.

## 4. Auto Scaling, Launch Templates and SNS

Definitions

- Auto Scaling: Automatically adjusts resource capacity based on demand or configuration.
- ASG: Auto Scaling Group, maintains and scales a group of EC2 instances.
- Launch Template: Stores EC2 launch configuration, such as AMI and instance type.
- SNS: Simple Notification Service, a managed publish/subscribe messaging service.
- Scaling Policy: Defines how capacity changes in response to metrics or other conditions.

Points to remember

- Minimum capacity: Lowest configured instance count.
- Desired capacity: Target number of instances.
- Maximum capacity: Highest configured instance count.
- Scale Out: Increase the number of instances.
- Scale In: Decrease the number of instances.
- SNS supports notification delivery through channels such as email and SMS.
- ASG can replace unhealthy instances.
- ASG can integrate with an Application Load Balancer.

Example: Minimum = 2, Desired = 3, Maximum = 5.

## 5. Amazon EBS

Definitions

- EBS: Elastic Block Store, persistent block storage primarily used with EC2.
- EBS Volume: A virtual block storage device.
- Root Volume: Storage containing the operating system.
- IOPS: Input/output operations per second.
- gp3: General Purpose SSD EBS volume type.

Points to remember

- EBS volumes are created in a specific Availability Zone.
- A standard EBS volume must be attached to an instance in the same AZ.
- EBS persists independently of the EC2 instance lifecycle, subject to deletion settings.
- EBS supports resizing volumes.
- EBS volume types include gp3, io2, st1 and sc1.
- An EBS volume generally attaches to one instance at a time; supported Multi-Attach configurations are exceptions.

## 6. EBS Snapshots

Definitions

- Snapshot: A point-in-time backup of an EBS volume.
- Incremental Backup: Stores changed blocks after the initial snapshot.
- Volume Restore: Creates a new EBS volume from a snapshot.

Points to remember

- EBS snapshots are incremental.
- Snapshots can be copied across Regions.
- Snapshots can be shared across AWS accounts subject to permissions and encryption restrictions.
- Snapshots are used for backup and disaster recovery.
- Snapshots are stored in AWS-managed storage backed by S3, not as ordinary user-visible S3 objects.
- Snapshots and AMIs are different: a snapshot backs up volume data; an AMI provides a launch template.

## 7. Amazon S3 Fundamentals

Definitions

- S3: Simple Storage Service, an object storage service.
- Bucket: A container for storing S3 objects.
- Object: Data stored in S3, consisting of content and metadata.
- Object Key: The identifier of an object within a bucket.
- Presigned URL: A time-limited URL granting access to an S3 operation using the signing principal's permissions.
- Static Website Hosting: Serving static website content such as HTML, CSS and JavaScript.

Points to remember

- S3 is object storage, not block storage.
- S3 is regional, with data stored redundantly across multiple AZs by default for standard storage.
- S3 supports object versioning.
- S3 supports presigned URLs.
- S3 static website endpoints support HTTP, not HTTPS directly.
- S3 Block Public Access should remain enabled unless public access is deliberately required and safely configured.
- S3 Standard is designed for 99.999999999% (11 nines) object durability.

## 8. S3 Versioning, Replication and Lifecycle

Definitions

- Versioning: Maintains multiple versions of an object.
- CRR: Cross-Region Replication, replicating objects between buckets in different Regions.
- SRR: Same-Region Replication, replicating objects within one Region.
- Lifecycle Rule: Automates object transitions or expiration.
- Storage Class: A storage option based on access frequency, performance and cost.

Important S3 storage classes

| Storage class              | Primary use                             |
| -------------------------- | --------------------------------------- |
| S3 Standard                | Frequently accessed data                |
| Intelligent-Tiering        | Changing or unknown access patterns     |
| Standard-IA                | Infrequently accessed data              |
| One Zone-IA                | Infrequently accessed, recreatable data |
| Glacier Instant Retrieval  | Archive with millisecond retrieval      |
| Glacier Flexible Retrieval | Archive with flexible retrieval times   |
| Glacier Deep Archive       | Long-term, rarely accessed archives     |

Points to remember

- Versioning protects against accidental overwrites and helps recover deleted objects.
- CRR requires versioning on source and destination buckets.
- Lifecycle rules help optimize storage costs.
- Archived objects may require restoration before they can be accessed.
- Replication is not a replacement for a complete backup strategy.

## 9. Amazon RDS and MySQL

Definitions

- Database: An organized collection of data.
- RDBMS: Relational Database Management System.
- RDS: Relational Database Service, a managed database service.
- MySQL: A relational database management system.
- SQL: Structured Query Language.
- Primary Key: A column or set of columns uniquely identifying each row.
- Multi-AZ: A deployment configuration supporting high availability.

Points to remember

- RDS supports engines such as MySQL, PostgreSQL, MariaDB, Oracle and SQL Server.
- MySQL default port: 3306.
- AWS manages many database infrastructure tasks in RDS.
- Multi-AZ is primarily for high availability.
- Read Replicas help scale read workloads.
- SQL `CREATE TABLE` creates a table.
- SQL `INSERT INTO` inserts records.
- SQL `SELECT` retrieves data.

## 10. AWS IAM

Definitions

- IAM: Identity and Access Management, used to control access to AWS resources.
- IAM User: An identity representing a person or workload in an AWS account.
- IAM Group: A collection of IAM users.
- IAM Role: An identity with permissions that can be assumed temporarily.
- IAM Policy: A JSON document defining permissions.
- MFA: Multi-Factor Authentication.
- Root User: The original account identity with unrestricted account-level access.

Points to remember

- IAM is a global service.
- IAM policies commonly use `Effect`, `Action` and `Resource`.
- Explicit Deny overrides Allow.
- Access is implicitly denied unless allowed by applicable policies.
- Apply the principle of least privilege.
- Enable MFA for the root user and human users.
- IAM roles commonly provide temporary credentials.
- Avoid using root credentials for everyday administration.

## 11. CloudWatch and CloudTrail

Definitions

- CloudWatch: AWS monitoring and observability service for metrics, logs, alarms and more.
- CloudTrail: Records AWS account activity and API events.
- Metric: A time-series measurement.
- Alarm: Monitors a metric or expression and changes state based on configured conditions.
- Trail: A CloudTrail configuration delivering events to storage or analysis destinations.

| CloudWatch                          | CloudTrail                              |
| ----------------------------------- | --------------------------------------- |
| Monitors metrics and logs           | Records API and account activity        |
| Supports alarms                     | Supports auditing                       |
| Helps identify performance problems | Helps investigate who performed actions |
| Example: CPU utilization            | Example: `RunInstances` API event       |

Points to remember

- CloudWatch is commonly used for operational monitoring.
- CloudTrail is commonly used for auditing and security investigation.
- CloudWatch alarms can trigger SNS notifications.
- CloudTrail records management events and can be configured for data events.
- Both services can contribute to security monitoring.

## 12. Amazon VPC and Networking

Definitions

- VPC: Virtual Private Cloud, a logically isolated virtual network in AWS.
- Subnet: A range of IP addresses within a VPC, associated with one AZ.
- Public Subnet: A subnet whose route table has a route to an Internet Gateway.
- Private Subnet: A subnet without a direct route to an Internet Gateway.
- Internet Gateway (IGW): Enables internet connectivity for resources with suitable routes and addresses.
- NAT Gateway: Enables outbound connectivity for private resources without accepting unsolicited inbound internet connections.
- Route Table: A set of rules controlling network traffic routing.
- CIDR: Classless Inter-Domain Routing, a method for expressing IP address ranges.

Points to remember

- VPCs span Availability Zones within one Region.
- Subnets belong to one AZ.
- A public IPv4 address alone does not guarantee internet access.
- Public subnet route example: `0.0.0.0/0 → IGW`.
- Private subnet outbound route example: `0.0.0.0/0 → NAT Gateway`.
- NAT Gateway is commonly placed in a public subnet.
- Route tables determine where packets are forwarded.

Basic VPC Architecture

Internet

Internet Gateway

VPC – 10.0.0.0/16

Public Subnet

10.0.1.0/24

Public EC2

NAT Gateway

Private Subnet

10.0.2.0/24

Private EC2

Database

Private EC2 → NAT Gateway → Internet Gateway → Internet (outbound)

## 13. VPC Peering

Definitions

- VPC Peering: A private network connection between two VPCs.
- Peering Requester: The VPC initiating a peering request.
- Peering Accepter: The VPC accepting the request.
- Non-Transitive Routing: Traffic cannot automatically pass through one peered VPC to reach another.

Points to remember

- VPC Peering supports same-Region and cross-Region connectivity.
- Peered VPCs cannot have overlapping IPv4 CIDR ranges.
- Route tables must include appropriate routes.
- Security Groups and NACLs must allow the traffic.
- VPC Peering does not support transitive routing.

## 14. CIDR, NACL and Security Groups

Definitions

- Security Group: A stateful virtual firewall controlling traffic at the network interface level.
- NACL: Network Access Control List, a stateless firewall controlling subnet traffic.
- CIDR Notation: An IP network address followed by a prefix length, such as `10.0.0.0/24`.
- Ephemeral Port: A temporary port used by a client connection.

| Feature        | Security Group                                | NACL                         |
| -------------- | --------------------------------------------- | ---------------------------- |
| State          | Stateful                                      | Stateless                    |
| Level          | Network interface                             | Subnet                       |
| Rules          | Allow only                                    | Allow and Deny               |
| Evaluation     | All applicable rules                          | Ascending rule number        |
| Return traffic | Automatically allowed for tracked connections | Must be explicitly permitted |

Points to remember

- `/24` represents 256 IPv4 addresses.
- `/16` represents 65,536 IPv4 addresses.
- AWS reserves five IPv4 addresses per subnet.
- `0.0.0.0/0` represents all IPv4 addresses.
- NACL rules are processed in ascending rule-number order.
- A Security Group cannot have an explicit Deny rule.
- NACLs require appropriate inbound and outbound rules.

## 15. Amazon Route 53

Definitions

- Route 53: AWS DNS web service supporting domain registration, DNS routing and health checks.
- DNS: Domain Name System, translates domain names into records such as IP addresses.
- A Record: Maps a hostname to an IPv4 address.
- AAAA Record: Maps a hostname to an IPv6 address.
- CNAME: Maps one hostname to another hostname.
- Alias Record: Route 53-specific record that can point to supported AWS resources.
- TTL: Time To Live, controls DNS caching duration.

Points to remember

- Route 53 supports domain registration.
- Route 53 supports public and private hosted zones.
- An A record can point to an EC2 public IPv4 address.
- An Alias record can point to an ALB.
- CNAME records cannot be created at the zone apex.
- Routing policies include Simple, Weighted, Latency, Failover and Geolocation.

## 16. AWS CloudFormation and Lightsail

Definitions

- IaC: Infrastructure as Code, managing infrastructure through configuration files.
- CloudFormation: AWS service for provisioning infrastructure using templates.
- Template: JSON or YAML document describing infrastructure.
- Stack: A collection of AWS resources managed as one CloudFormation unit.
- Change Set: A preview of proposed stack changes.
- Lightsail: A simplified AWS service offering virtual servers and related resources.

Points to remember

- CloudFormation templates can be written in YAML or JSON.
- Common sections include `Parameters`, `Resources` and `Outputs`.
- `Resources` is the main section defining infrastructure.
- CloudFormation can create EC2 instances, S3 buckets and other supported resources.
- CloudFormation supports stack updates and rollback behavior.
- Lightsail is useful for simpler website and application deployments.

## 17. Amazon DynamoDB

Definitions

- DynamoDB: A fully managed, serverless NoSQL database service.
- Table: A collection of items.
- Item: A collection of attributes.
- Attribute: An individual data element.
- Partition Key: A key attribute used to determine data placement.
- Sort Key: An optional key attribute used with a partition key.
- On-Demand Capacity: Capacity mode that automatically accommodates workload demand.

Points to remember

- DynamoDB is a NoSQL database.
- DynamoDB does not require fixed schemas for non-key attributes.
- Every item must have a primary key.
- Primary keys can be simple or composite.
- DynamoDB supports low-latency reads and writes.
- DynamoDB supports both on-demand and provisioned capacity modes.

## 18. AWS Lambda

Definitions

- Lambda: A serverless compute service that runs code in response to events or invocations.
- Function: Code and configuration deployed to Lambda.
- Trigger: An event source or configuration that invokes a function.
- Execution Role: An IAM role granting the function permissions to AWS resources.
- Timeout: Maximum duration allowed for a function invocation.
- Cold Start: Initialization work needed when a new execution environment starts.

Points to remember

- Lambda does not require users to manage servers.
- Lambda supports runtimes including Python, Node.js and Java.
- Maximum function execution duration is 15 minutes.
- Lambda can integrate with S3, API Gateway, EventBridge and DynamoDB.
- Lambda pricing commonly depends on requests and execution resource usage.
- Lambda is suited to event-driven applications.

## 19. AWS Elastic Beanstalk

Definitions

- Elastic Beanstalk: A managed service for deploying and operating web applications.
- Application: A logical collection of application versions and environments.
- Environment: A deployment of an application version onto AWS resources.
- Environment Cloning: Creates a new environment using an existing environment's configuration.
- CNAME Swap: Exchanges environment URLs between two Elastic Beanstalk environments.

Points to remember

- Elastic Beanstalk simplifies application deployment.
- It provisions and manages supporting AWS resources.
- It supports platforms such as Java, Python, Node.js and .NET.
- Environment cloning is useful for testing and migration.
- CNAME swapping can support blue-green deployment strategies.
- Users retain responsibility for application code and relevant AWS resource costs.

## Quick Revision: AWS Important Ports

| Service              | Port | Protocol |
| -------------------- | ---- | -------- |
| SSH                  | 22   | TCP      |
| RDP                  | 3389 | TCP      |
| HTTP                 | 80   | TCP      |
| HTTPS                | 443  | TCP      |
| MySQL                | 3306 | TCP      |
| PostgreSQL           | 5432 | TCP      |
| DNS                  | 53   | UDP/TCP  |
| Microsoft SQL Server | 1433 | TCP      |

## 15 Most Important Exam Points

1. EC2 provides virtual servers.
2. S3 provides object storage.
3. EBS provides block storage.
4. RDS provides managed relational databases.
5. DynamoDB provides managed NoSQL databases.
6. IAM controls identities and permissions.
7. VPC provides logically isolated networking.
8. Security Groups are stateful.
9. NACLs are stateless.
10. ALB operates at Layer 7.
11. Auto Scaling adjusts EC2 capacity.
12. CloudWatch monitors metrics, logs and alarms.
13. CloudTrail records AWS API and account activity.
14. Route 53 provides DNS services.
15. CloudFormation automates infrastructure provisioning.

## Test Your Knowledge

AWS Knowledge Check

0 of 5 answered

1\. Which AWS service provides object storage?

Amazon EBS

Amazon S3

Amazon EC2

Amazon RDS

2\. Which security control is stateless?

Security Group

IAM Policy

Network ACL

IAM Role

3\. Which port is used by RDP?

22

80

443

3389

4\. Which service records AWS API activity?

CloudTrail

CloudWatch

SNS

Route 53

5\. What is the maximum AWS Lambda invocation duration?

5 minutes

15 minutes

30 minutes

60 minutes

Check AnswersReset

These notes cover all the major syllabus headings, with special emphasis on definitions, differences between services, ports, networking and frequently tested concepts.
