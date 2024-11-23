How many environments does application have? Is there a DR? Do we have RTO / RPO timelines?
Is there CI/CD already available for the apps? What is the DevOps tool stack being used?
Application Testing strategy
Was a cost assessment of this migration already performed?
Will VMware provide necessary support during the course of migration?
Is version upgrade of tools / databases / frameworks required to be performed?
Are there applications / tools that cannot run / not compatible on a Virtual environment?
What is the process followed to patch servers or patch management?
Will there be a dedicated team who will address issues and challenges faced by Virtusa during migration activity. What level of support will be provided teams like Networking, Operations, DNS, 3rd-party etc.
Must application undergo Architecture Review Board approval for any design changes, necessitated because of the migration?
How are applications and infrastructure monitored?
Are storage network drives impacted by this migration?
Are there any specific KPIs that need to be tracked for migration?
Is additional network segmentation required or what are the changes in the networking architecture?
How is user access to application and infrastructure managed?
Are there applications that require scaling?
Is there a requirement to do Pilot migration before a full-scale or phased approach?
Understanding the Change management process.
What monitoring tools are being used?
What is the driving force for moving to a private cloud (e.g., cost reduction, scalability, security, performance)?
What applications and services are currently running in your data centre? ( Java, .Net, Mainframe, COTS, SFDC, PEGA? Database: MSSQL, Oracle?)
What types of workloads will be moved (e.g., databases, data, web applications, analytics)?
Since this involves, multi-country decentralization, is their any compliance requirements risk for this migration (e.g., HIPAA, GDPR, PCI-DSS)
What are your current performance benchmarks, and are their any challenges / bottlenecks currently with this applications and what is the expectation through this migration?
What is the user volume?
How many applications in scope and how many VM’s tentatively?
Is the applications or internal system or external facing?
Do we have internal or third party integrations and how many of them? Are there any challenges maintaining the same integration?
How much is the volume of the data ? Are there any data backup solutions that's currently used?
Will you manage networking between your private cloud and on-premises or other clouds?
Do you have any tools license dependencies?
Do you have any timelines in mind to complete this migration?
What potential challenges or risks do you foresee with this migration?
Are there any business-critical systems that cannot experience downtime?
Our understanding is we are using VMWARE as the hypervisors currently ?
Have you previously used VMware products, and if so, which ones (e.g., vSphere, NSX, vSAN, vCenter)?
Do you have any preferences for specific VMware components or features? Or is this been well defined?
Is the IT, business leaders, and key stakeholders aligned on this initiative?
What security framework is used currently

What is the current API types followed E.g. REST, GraphQL, SOAP, gRPC	
Is there a plan to add new API types?	
Does API used just for Internal or External or Third party integrations	
Is there versioning of the API's for easy rollback?	
How is the current policies and processes for controlling user identities E.g. (Api Keys, OAuth, JWT)	
How is the current policies and processes for controlling access rights ( AWS Cognito)	
What are the various roles and permission	
Do you have MFA in Place?	
What is the alert mechanism	
What is the logging mechanism ( API CloudWatch, CloudWatch metrics)	
How is Firewall Setup and what are the various Rules? ( AWS WAF)	
How is Data Encrypted?	
How is data secured in transit (TSL, SSL)	
Are there any Rate Limiting, throttling setup?	
Are there any IP whitelisting	
How is the IAM governed	
Is there any cross account API Access	
How is vulnerability managed? ( Guardduty or inspector)	
What is the current API Response time	
Are there any latency issues observed	
What is the current throughput	
How scalable are they today? ( HZ or Vertical)	
How is the documentation API today	
Are their testing pipelines or tools being used?	
Are their API caching mechanism implemented?	
How frequently the API's are managed and governed	
Are their deprecated endpoints	
how do you manage cross Account API Access	
Is API, domain driven or event driven today	
How Is API decoupled from Infra?	
Are their any circuit breakers implemented?	
How is downtime managed?	
How is downtime communicated?	
Do you have an informative UI/ UX currently? ( Search and Browse)	
Do we have enough tools for the developers to validate the API( Swagger, OPEN API)	
Sample code for integration progress?- Quick start Guides	
Do you have Robust  Filters to narrow down the API	
Do you have the API resources logically grouped	
Does all the API's have Consistent naming	
Do you have Sandbox Environment to test the API	
Are you planning to have external users use them at price?	
Is the API's are compliant to legal regulations?	
Do you have provider and consumer insight dashboards?	
Provide opportunity for developers to interact with the community	
How is the helpdesk managed today?	
Are you planning this API's for global user base	
Does Lambda functions have single responsibility principle?	
How many lambda functions are there?	
What is the use of edge	
How is timeout and memory allocation based on workload	
How is the security stored safely	
any queuing services used?	
how is feedback gathered from the users?	



AWS Well Architected Framework			
Operational Excellence		1)Verify the use of monitoring tools like CloudWatch, X-Ray, or third-party solutions.
2)Check if CI/CD pipelines are in place for deployment automation (e.g., CodePipeline, Jenkins).
  - Ensure runbooks and playbooks exist for common operational tasks.	
Design for Operations	Is the application designed for efficient and scalable operations	1)Verify the use of monitoring tools like CloudWatch, X-Ray, or third-party solutions.
2)Check if CI/CD pipelines are in place for deployment automation (e.g., CodePipeline, Jenkins).
  - Ensure runbooks and playbooks exist for common operational tasks.	
Automate Processes	Are processes such as deployment, monitoring, and recovery automated?	1)Verify the use of monitoring tools like CloudWatch, X-Ray, or third-party solutions.
2)Check if CI/CD pipelines are in place for deployment automation (e.g., CodePipeline, Jenkins).
  - Ensure runbooks and playbooks exist for common operational tasks.	
Monitor and Respond	Are metrics and logs being collected and analyzed to ensure proper operations? Is there a strategy for incident response?	1)Verify the use of monitoring tools like CloudWatch, X-Ray, or third-party solutions.
2)Check if CI/CD pipelines are in place for deployment automation (e.g., CodePipeline, Jenkins).
  - Ensure runbooks and playbooks exist for common operational tasks.	
Improve Continously	Are operational processes regularly reviewed and improved?	1)Verify the use of monitoring tools like CloudWatch, X-Ray, or third-party solutions.
2)Check if CI/CD pipelines are in place for deployment automation (e.g., CodePipeline, Jenkins).
  - Ensure runbooks and playbooks exist for common operational tasks.	
Security			
Identity and Access Management	Are least privilege principles being followed? Are access controls like IAM roles and policies correctly implemented?	Review IAM policies, ensure multifactor authentication (MFA) is enforced, and check the least privilege principle
Verify that encryption (e.g., KMS) is applied where necessary.
Ensure VPC, security group, and network configuration follow best practices for network security.
Check AWS services like GuardDuty, AWS WAF, and Config for security assessments	
Data Protection	Is sensitive data encrypted both at rest and in transit	Review IAM policies, ensure multifactor authentication (MFA) is enforced, and check the least privilege principle
Verify that encryption (e.g., KMS) is applied where necessary.
Ensure VPC, security group, and network configuration follow best practices for network security.
Check AWS services like GuardDuty, AWS WAF, and Config for security assessments	
Detective Controls	Are logging and monitoring implemented to detect security incidents	Review IAM policies, ensure multifactor authentication (MFA) is enforced, and check the least privilege principle
Verify that encryption (e.g., KMS) is applied where necessary.
Ensure VPC, security group, and network configuration follow best practices for network security.
Check AWS services like GuardDuty, AWS WAF, and Config for security assessments	
Infrastructure Security	Are the right security controls in place, such as firewalls, security groups, and VPNs?	Review IAM policies, ensure multifactor authentication (MFA) is enforced, and check the least privilege principle
Verify that encryption (e.g., KMS) is applied where necessary.
Ensure VPC, security group, and network configuration follow best practices for network security.
Check AWS services like GuardDuty, AWS WAF, and Config for security assessments	
Reliability			
Foundations	Are the basic components, such as networking and DNS, well-architected for reliability?	Ensure the architecture is designed with redundancy and failover mechanisms (e.g., multi-AZ, auto-scaling).
  - Validate the existence of backup plans and disaster recovery strategies (e.g., AWS Backup, automated snapshots).
  - Check for the use of Route 53 health checks and failover configurations.	
Change Management	Are changes to infrastructure controlled and managed to minimize the impact of failures?	Ensure the architecture is designed with redundancy and failover mechanisms (e.g., multi-AZ, auto-scaling).
  - Validate the existence of backup plans and disaster recovery strategies (e.g., AWS Backup, automated snapshots).
  - Check for the use of Route 53 health checks and failover configurations.	
Failure Recovery	Is there an ability to recover quickly from failures? Are backups and disaster recovery plans in place?	Ensure the architecture is designed with redundancy and failover mechanisms (e.g., multi-AZ, auto-scaling).
  - Validate the existence of backup plans and disaster recovery strategies (e.g., AWS Backup, automated snapshots).
  - Check for the use of Route 53 health checks and failover configurations.	
Scalability and Availability	Are scalable architectures like Auto Scaling and Elastic Load Balancers implemented?	Ensure the architecture is designed with redundancy and failover mechanisms (e.g., multi-AZ, auto-scaling).
  - Validate the existence of backup plans and disaster recovery strategies (e.g., AWS Backup, automated snapshots).
  - Check for the use of Route 53 health checks and failover configurations.	
Performance			
Flexible Compute	Are appropriate compute resources used (e.g., EC2, Lambda, ECS) based on workload requirements?	1)Verify that instances and storage are right-sized for the workload.
2)Ensure there are scaling policies in place that adjust resources based on demand.
3)Check the use of caching mechanisms (e.g., CloudFront, ElastiCache) to optimize performance	
Storage Optimization	Are the right storage solutions (e.g., S3, EBS, RDS) used based on performance and cost?	1)Verify that instances and storage are right-sized for the workload.
2)Ensure there are scaling policies in place that adjust resources based on demand.
3)Check the use of caching mechanisms (e.g., CloudFront, ElastiCache) to optimize performance	
Monitoring and Adaptation	Are workload performance metrics monitored to ensure efficiency?	1)Verify that instances and storage are right-sized for the workload.
2)Ensure there are scaling policies in place that adjust resources based on demand.
3)Check the use of caching mechanisms (e.g., CloudFront, ElastiCache) to optimize performance	
Scaling	Are automatic scaling mechanisms in place to handle demand (e.g., Auto Scaling, AWS Lambda’s scaling behavior)?	1)Verify that instances and storage are right-sized for the workload.
2)Ensure there are scaling policies in place that adjust resources based on demand.
3)Check the use of caching mechanisms (e.g., CloudFront, ElastiCache) to optimize performance	
Cost Optimization			
Eliminate Unused Resources	Are idle or unused resources being identified and eliminated	Review cost reports and budgeting tools (e.g., AWS Cost Explorer, Budgets) to ensure cost visibility and tracking.
  - Check for unused or underutilized resources, such as idle EC2 instances or oversized RDS databases.
  - Ensure S3 lifecycle policies are in place to manage data storage costs.	
Right-Sizing	Are resources (compute, storage, etc.) right-sized to match workload needs?	Review cost reports and budgeting tools (e.g., AWS Cost Explorer, Budgets) to ensure cost visibility and tracking.
  - Check for unused or underutilized resources, such as idle EC2 instances or oversized RDS databases.
  - Ensure S3 lifecycle policies are in place to manage data storage costs.	
Leverage Reserved Pricing	Are Reserved Instances, Savings Plans, or spot instances used to optimize costs?	Review cost reports and budgeting tools (e.g., AWS Cost Explorer, Budgets) to ensure cost visibility and tracking.
  - Check for unused or underutilized resources, such as idle EC2 instances or oversized RDS databases.
  - Ensure S3 lifecycle policies are in place to manage data storage costs.	
Efficient Data Transfer	Are unnecessary data transfer costs minimized (e.g., by using CloudFront for content delivery)	Review cost reports and budgeting tools (e.g., AWS Cost Explorer, Budgets) to ensure cost visibility and tracking.
  - Check for unused or underutilized resources, such as idle EC2 instances or oversized RDS databases.
  - Ensure S3 lifecycle policies are in place to manage data storage costs.	
Sustainability			
Region Selection			
Alignment to Demand			
Data Management			
GAP Analysis			
Remediation and Improvement			



Can you explain the Business use case for the api gateway
Can you explain the application use case with multiple api services
How the data will be transferred to the application
What is the authentication service in the architecture
Can you explain more into cognito / okta services….
How is the use case of dynamodb
How is the ‘dynamodb’  configured as multi regional data source
How is the route53/cloudfront integrated in the architecture
What is the purpose of the Lambda Edge in the architecture
More info about gateway (Primary and secondary Information)
How gateways communication is configured in the multi region
What is the use case of api gateway interconnected in the architecture
What is the purpose of Lambda between Gateway and EKS
How was the application is configured on EKS/ Containers
What is the use case of improvement of API gateway into centralized gateway
Who are the end users accessing the application
What is the use of external region / out side of AWS Cloud 
Size of DB and read or write, no of transactions

A) What they have done so far? What is the purpose
B) What is that Circle in the top means?
C) Route 53- CloudFront ( Why they are using Lambda Edge)
D) What is the purpose of DynamoDB and what is getting pulled from DynamoDB
E) Multi Regional Data source- DynamoDB has global tables or region specific ?
F) Why there is three regions and why one is outside AWS
G) Which is primary region
H) What is the traffic channel setup? how they are utilizing the other regions as well
I) Why API gateways arrow
J) EKS or ECS? ( Does not look like AWS Service. Blue Item)
K) API Gateway to ECS is there but not sure AKS?
L) What about authentication mechanism used?
M) What is the system above?
N) who are all the consumers?
O)what is the API does?
P)who are the consumers?
Q)who are the users
R)what is centralized APIGATEWAY mean
S)Cognito is good enough, why do we need Okta?
T)size of DB, for what are they used>, volume of transactions, read or write?
U)SAM is used. Centralized might need to be relook at
V)Current AWS organization set up
W)ahow many environments?
