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

**Be sure to cover the following topics**

**- Whitepapers are the key to understand**
	- [Overview of Security Processes](https://tunglouis.github.io)
	- [Disaster Recovery](https://tunglouis.github.io) (Note: `make sure you understand the difference between each types esp. pilot light, warm standby w.r.t RTO and RPO`)
	- [Cloud migration](https://tunglouis.github.io) (Note `make sure you understand the difference between rehost, replatform, rearchitect`)
	- [Architecting for the Cloud: Best Practices](https://tunglouis.github.io)
	- [Building Fault-Tolerant Application on AWS](https://tunglouis.github.io)
**- Migration & Transfer**
	- Understand [Cloud Migration Services](https://tunglouis.github.io)
	- Know Server Migration Service
	- Know Database Migration Service (Hint `Elasticsearch is supported by DMS`)
	- Know Snowball vs Snowball Edge vs SnowMobile
	- Know AWS [Application Discovery Service](https://tunglouis.github.io) (Hint `agentless mode does not track processes`)
**- Management & Governance tools**
	- Understand [AWS Organizations](https://tunglouis.github.io)
		- Know the difference between [Service Control Policies and IAM Policies](https://tunglouis.github.io) (Hint `SCP is the maximum permission that an user can have, however the user needs to be explicitly given IAM policy`)
	- [Systems Manager](https://tunglouis.github.io)
		- Understand AWS Systems Manager and its various services like parameter store, patch manager
		- Understand the [Systems Manager Patch Manager patching process](https://tunglouis.github.io)
	- Understand [Cloudwatch](https://tunglouis.github.io)
		- Understand [Cloudwatch logs](https://tunglouis.github.io)
		- Understand [CloudWatch Subscription Filters](https://tunglouis.github.io) and its integration with other services.
		- Understand [CloudWatch Events](https://tunglouis.github.io)
	- Understand [CloudTrail](https://tunglouis.github.io) for audit and governance
	- Know [CloudFormation](https://tunglouis.github.io) esp. in terms of Disaster recovery to replicate environment across regions.
	- Exam does not cover developer tools like CodeDeploy, CodeCommit, CodePipeline, CodeBuild
**- Networking & Content Delivery**
	- Know [VPC](https://tunglouis.github.io)
		- Understand [Security Groups, NACLs](https://tunglouis.github.io) (Hint `know NACLs are stateless`)
		- Understand [VPC Endpoints](https://tunglouis.github.io) (Hint `know how to restrict access on S3 to specific VPC Endpoint`)
		- Understand [VPC Flow Logs](https://tunglouis.github.io)
		- Understand [VPC Peering](https://tunglouis.github.io)
	- Route 53
		- Understand [Route 53](https://tunglouis.github.io)
		- Understand [Routing Policies](https://tunglouis.github.io) and their use cases Focus on Weighted, Latency routing poicies
	- Understand [CloudFront](https://tunglouis.github.io) and use cases (Hint `S3 caching`)
	- Understand [API Gateway](https://tunglouis.github.io)
	- Know AWS [PrivateLink](https://tunglouis.github.io) (Hint `can be used to exposed microservices within the AWS network`)
	- Load Balancer
		- Understand [ELB](https://tunglouis.github.io), [ALB](https://tunglouis.github.io) and [NLB](https://tunglouis.github.io)
		- Understand [ELB with Auto Scaling](https://tunglouis.github.io)

