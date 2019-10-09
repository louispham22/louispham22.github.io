---
layout: post
title:  "AWS Certified Solution Architect – Professional (SAP-C01) Exam Learning Path"
date:   2019-10-08 16:30
categories: AWS-training
permalink: /archivers/aws-certified-solution-architect-professional
---

**AWS Certified Solution Architect – Professional (SAP-C01) Exam Learning Path**

AWS Certified Solutions Architect - Professional (SAP-C01) exam is the upgraded pattern of the previous Solution Architect - Professional exam which was released last year (2018) and upgraded this year.

AWS Certified Solution Architect - Professional (SAP-C01) exam basically validates

	- Design and deploy denamically scalable, highly available, fault-tolerant, 
	and reliable application on AWS
	- Select appropriate AWS services to design and deploy an application based 
	on given requirements
	- Migrate complex, multi-tier applications on AWS
	- Design and deploy enterprise-wide scalable operations AWS
	- Implement cost-control strategies

[Refer to AWS Certified Solutions Architect – Professional Exam Guide](https://d1.awsstatic.com/training-and-certification/docs-sa-pro/AWS_Certified_Solutions_Architect_Professional-Exam_Guide_EN_1.2.pdf)

![AWS-Certified-Solutions-Architect-Professional](../../images/AWS-Certified-Solutions-Architect-Professional-SAP-C01-Exam-Domains-1024x305.png)

AWS Certified Solutions Architect – Professional (SAP-C01) Exam Summary

- AWS Certified Solutions Architect – Professional (SAP-C01) exam was for a total of *170 minutes but it had 75 questions*. The questions and answers options are quite long and there is a lot of reading that needs to be done, so be sure you are prepared and manage your time well. As always, mark the questions for review and move on and come back to them after you are done with all.
- One of the key tactic I followed when solving any question was to read the question and use paper and pencil to draw a rough architecture and focus on the areas that you need to improve. Trust me, you will be able eliminate 2 answers for  sure and then need to focus on only the other two. Read the other 2 answers to check the difference area and that would help you reach to the right answer  or atleast have a 50% chance of getting it right.
- AWS Certified Solutions Architect – Professional (SAP-C01) focuses a lot on concepts and services related to Scalability, High Availability, Disaster Recovery, Migration, Security and Cost Control.

Be sure to cover the following topics:

**Whitepapers are the key to understand**
  * [Overview of Security Processes](https://tunglouis.github.io)
  * [Disaster Recovery](https://tunglouis.github.io) (Hint: `make sure you understand the difference between each types esp. pilot light, warm standby w.r.t RTO and RPO`)
  * [Cloud migration](https://tunglouis.github.io) (Hint: `make sure you understand the difference between rehost, replatform, rearchitect`)
  * [Architecting for the Cloud: Best Practices](https://tunglouis.github.io)
  * [Building Fault-Tolerant Application on AWS](https://tunglouis.github.io)

**Migration & Transfer**
  * Understand **[Cloud Migration Services]**(https://tunglouis.github.io)
  * Know Server Migration Service
  * Know Database Migration Service (Hint: `Elasticsearch is supported by DMS`)
  *  Know Snowball vs Snowball Edge vs SnowMobile
  * Know AWS [Application Discovery Service](https://tunglouis.github.io) (Hint: `agentless mode does not track processes`)

**Management & Governance tools**

  * Understand [AWS Organizations](https://tunglouis.github.io)
    * Know the difference between [Service Control Policies and IAM Policies](https://tunglouis.github.io) (Hint: `SCP is the maximum permission that an user can have, however the user needs to be explicitly given IAM policy`)
  * [Systems Manager](https://tunglouis.github.io)
    * Understand AWS Systems Manager and its various services like parameter store, patch manager
    * Understand the [Systems Manager Patch Manager patching process](https://tunglouis.github.io)
  * Understand [Cloudwatch](https://tunglouis.github.io)
    * Understand [Cloudwatch logs](https://tunglouis.github.io)
    * Understand [CloudWatch Subscription Filters](https://tunglouis.github.io) and its integration with other services.
    * Understand [CloudWatch Events](https://tunglouis.github.io)
  * Understand [CloudTrail](https://tunglouis.github.io) for audit and governance
  * Know [CloudFormation](https://tunglouis.github.io) esp. in terms of Disaster recovery to replicate environment across regions.
  * Exam does not cover developer tools like CodeDeploy, CodeCommit, CodePipeline, CodeBuild

**Networking & Content Delivery**

  * Know [VPC](https://tunglouis.github.io)
    * Understand [Security Groups, NACLs](https://tunglouis.github.io) (Hint: `know NACLs are stateless`)
    * Understand [VPC Endpoints](https://tunglouis.github.io) (Hint: `know how to restrict access on S3 to specific VPC Endpoint`)
    * Understand [VPC Flow Logs](https://tunglouis.github.io)
    * Understand [VPC Peering](https://tunglouis.github.io)
  * Route 53
    * Understand [Route 53](https://tunglouis.github.io)
    * Understand [Routing Policies](https://tunglouis.github.io) and their use cases Focus on Weighted, Latency routing poicies
  * Understand [CloudFront](https://tunglouis.github.io) and use cases (Hint: `S3 caching`)
  * Understand [API Gateway](https://tunglouis.github.io)
  * Know AWS [PrivateLink](https://tunglouis.github.io) (Hint: `can be used to exposed microservices within the AWS network`)
  * Load Balancer
    * Understand [ELB](https://tunglouis.github.io), [ALB](https://tunglouis.github.io) and [NLB](https://tunglouis.github.io)
    * Understand [ELB with Auto Scaling](https://tunglouis.github.io)

**Security, Identity & Compliance**
  * AWS Identity and Access Management
    * Understand [IAM Roles](https://tunglouis.github.io) and user cases
    * Understand [IAM Web Identity & Federation](https://tunglouis.github.io)
    * Know [IAM Best Practices](https://tunglouis.github.io)
  * Know AWS Shield, WAF for DDoS Protection

**Storage**
  * Exam does not cover Storage services in deep
  * Focus on [Simple Secure Service](https://tunglouis.github.io) (S3) (Hint: `Know S3 supports retrieval of partial content using Range Get requests`)
    * Understand [S3 Permissions](https://tunglouis.github.io) (Hint: `know S3 bucket policy to control access to VPC Endpoints`)
    * Understand [S3 Data Protection](https://tunglouis.github.io)
    * Understand [S3 Storage Classes](https://tunglouis.github.io) (Hint: `Glacier for archival`)
    * Understand [S3 Subresources](https://tunglouis.github.io) (Hint: `Requester Pays can allow you to host content, while the user of the content pays the transfer costs`)
    * Know S3 disaster recovery across region. (Hint: `cross region replocation`)
    * Know CloudFront for caching to improve performance
  * Elastic Block Store
    * Focus mainly on [EBS Backup](https://tunglouis.github.io) using snapshots for HA and Disaster recovery
  * Understand [Storage Gateway](https://tunglouis.github.io)

**Database**
  * Exam covers databases mainly in terms of Scalability, High Availability and Disaster Recovery.
  * Understand [RDS Multi-AZ vs Read Replicas](https://tunglouis.github.io) (hint: cross region replication and availability of data)
  * Know Aurora DR & HA using [Read Replicas](https://tunglouis.github.io) and [Global Database](https://tunglouis.github.io)
  * Know [DynamoDB](https://tunglouis.github.io)
    * Know [DynamoDB Streams](https://tunglouis.github.io) for tracking changes
    * DynamoDB Auto Scaling & [DAX](https://tunglouis.github.io) for caching (hint: know TTL which can expire the data)
    * [Improve performance – Best practices](https://tunglouis.github.io) (hint : one question for selection of keys)

**Compute**
  * Understand [EC2](https://tunglouis.github.io)
    * Understand [EC2 Instance Types](https://tunglouis.github.io)
    * Understand [EC2 Instance Purchase Types](https://tunglouis.github.io)
  * Understand [Auto Scaling](https://tunglouis.github.io)
  * Know [Elastic Beanstalk](https://tunglouis.github.io) mainly from the perspective of migration.
  * Understand [Lambda](https://tunglouis.github.io) (hint: know what it takes to run Lambda within an VPC and Lambda@Edge)
  * Exam did not cover anything of relevance relating to ECS and EKS

**Analytics**
  * Understand [Kinesis](https://tunglouis.github.io)
    * Understand the difference between Kinesis Data Streams and Kinesis Firehose
  * Know Amazon [Elasticsearch](https://tunglouis.github.io) provides a managed solution

**Integration Tools**
  * Understand [SQS](https://tunglouis.github.io) in terms of loose coupling and scaling.
    * Know the difference between [SQS Standard and FIFO](https://tunglouis.github.io)
  * Know how CloudWatch integration with [SNS](https://tunglouis.github.io) and [Lambda](https://tunglouis.github.io) can help in notification

**AWS Certified Solutions Architect – Professional (SAP-C01) Exam Resources**
  * Online Courses
    * DolfinEd [AWS Certified Solutions Architect – Professional 2019 course](https://www.udemy.com/course/amazon-certified-solutions-architect-professional/?couponCode=JAYPCSAPRO-15NEW) [Recommended]
  * Practice tests
    * Braincert [AWS Certified Solutions Architect – Professional Practice Exams](https://www.braincert.com/course/10323-AWS-Certified-Solutions-Architect-%E2%80%93-Professional-Practice-Exams) [Recommended] – This can help you a lot to practice and deep dive.