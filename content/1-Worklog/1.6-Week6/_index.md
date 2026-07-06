---
title: "Week 6 Worklog"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.6. </b> "
---
{{% notice warning %}} 

{{% /notice %}}


### Week 6 Objectives:

* Learn about Amazon RDS for PostgreSQL and the role of relational databases on AWS.
* Understand the process of creating, configuring, and managing a PostgreSQL database on Amazon RDS.
* Learn about data backup and recovery methods in Amazon RDS.
* Understand the mechanisms used to ensure high availability and disaster recovery.
* Practise assigning an IAM Role to an Amazon EC2 instance for secure access to AWS resources.

### Tasks to Be Completed This Week:

| Day       | Tasks                                                                                                                                                                                                                                                                                                                                                                                                                                                              | Start Date | Completion Date | Reference Materials                    |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | -------------------------------------- |
| Monday    | - Study **RDS PostgreSQL on AWS – Introduction**. <br> - Learn about the concept and role of Amazon Relational Database Service. <br> - Learn how Amazon RDS supports PostgreSQL. <br> - Learn about fundamental components such as DB Instances, DB Engines, Storage, and Endpoints. <br> - Learn the steps required to create and connect to a PostgreSQL database on Amazon RDS.                                                                                | 25/05/2026 | 25/05/2026      | https://www.youtube.com/@AWSStudyGroup |
| Tuesday   | - Study **RDS PostgreSQL on AWS – Backup and Restore**. <br> - Learn about Automated Backups and Manual Snapshots. <br> - Learn about backup retention periods. <br> - Learn about Point-in-Time Recovery. <br> - Learn how to restore a DB Instance from a Snapshot or an automated backup.                                                                                                                                                                       | 26/05/2026 | 26/05/2026      | https://www.youtube.com/@AWSStudyGroup |
| Wednesday | - Study **RDS PostgreSQL on AWS – High Availability and Disaster Recovery**. <br> - Learn about the Multi-AZ Deployment architecture. <br> - Learn about data synchronization and automatic failover mechanisms. <br> - Learn about Read Replicas and their use cases. <br> - Differentiate between High Availability and Disaster Recovery.                                                                                                                       | 27/05/2026 | 27/05/2026      | https://www.youtube.com/@AWSStudyGroup |
| Thursday  | - Complete the **Encryption with AWS Key Management Service (KMS)** lab. <br> - Practise creating and managing encryption keys using AWS KMS. <br> - Learn about AWS managed keys and customer managed keys. <br> - Practise encrypting and decrypting data. <br> - Learn about Key Policies and permissions for using encryption keys.                                                                                                                            | 28/05/2026 | 28/05/2026      | https://www.youtube.com/@AWSStudyGroup |
| Friday    | - Complete the **Access Control with IAM Policies and Conditions** lab. <br> - Learn how to use IAM Policies to control access permissions. <br> - Learn how to use the Condition element in an IAM Policy. <br> - Complete the **Instance Profiling with IAM Roles for EC2** lab. <br> - Practise creating an IAM Role and Instance Profile for EC2. <br> - Learn how an EC2 instance can access AWS services without storing Access Keys directly on the server. | 29/05/2026 | 29/05/2026      | https://www.youtube.com/@AWSStudyGroup |

### Week 6 Achievements:

* I understood the role of Amazon RDS in deploying and managing relational databases on AWS.

* I learned how Amazon RDS supports PostgreSQL and understood its fundamental components, including:

  * DB Instance
  * DB Engine
  * Storage
  * Endpoint
  * Security Group

* I understood the following data backup methods available in Amazon RDS:

  * Automated Backup
  * Manual Snapshot
  * Point-in-Time Recovery

* I learned how to restore a DB Instance from a Snapshot or an automated backup.

* I understood the role of Multi-AZ Deployment in ensuring high availability.

* I differentiated between High Availability and Disaster Recovery.

* I learned how Read Replicas support read scalability and reduce the workload on the primary database.

* I understood the role of AWS KMS in creating, managing, and using encryption keys.

* I understood how IAM Policies and Conditions can be used to control access permissions more precisely.

* I practised creating an IAM Role and Instance Profile for Amazon EC2.

* I understood how Amazon EC2 uses an IAM Role to access AWS services without storing an Access Key and Secret Access Key directly on the server.
