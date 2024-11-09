set up AWS organizations
org units
org scp and tag policies for parent and leaf (use policy staging account to see the effect of applying scp)
set-up qualsys and wiz
Set-up a base account. it should have
operation management
- cost reporting
- logging for s3 access and load balancer access
- observability for newrelic. link aws account to newrelic account 
security 
- cloudtrail log bucket to log everything that is happening
- cloudwatch to forward alarms to pagerduty. some of the alarms are 
- unauthorized api calls to detect malicious activity
- nomfaconsolesignin to increase visibility into single factor accounts not protected by MFA
- detect root usage to see its usage and how to prevent more logins.
- console sign-in failures to prevent brute force attack
- check disable or deleted cmk to prevent unusable data.
- prevent aws config recorder (better to be handled via scp)
- config to make sure resources are compliant and necessary remediation taken. use this places to check mandatory tags on all aws resources.
- conjur and cyberarks resources. custom provider written for both.
- kms to create base keys and permissions. keys can be used within the account.
- guard duty to send events to sumologic
- enable inspector on ec2 instances based on tags
- log-siem - send cloudtrail, vpcflowlogs and any other secure logs from instances to qradar. this is done through kinesis data stream.
- macie setup
- securityhub set-up 
- systems manager to enable maintenance windows for linux and windows patch
IAM 
- Create default service (linked) roles like for fargate
- IAM groups and roles (evens administrators). Link it to SSO also with permission sets
- IAM user for firecall
- Permission boundaries
- Default policies
- Roles required for third party integration, like new relic, kafka, RAM, sentry
(optional) when a new account is created, then a new tf org has to be created as well.
(deprecated) application specific customization. since running from management account it can apply specific resources to specific account.
Set-up a lob account. it should have
A CodeBuild pipeline to create base IMAGES for RHEL7, win2016/2019, jboss, amazon linux, centos, image for eks/ecs node using packer. build scripts are located in github that kicks off codebuild.
security
iam
compute
- create VPC, subnets, route tables, nacl, security group, nat gatreways, internet gateway, db subnet, cw log group, EIP, flow logs, VPC endpoints to resources in scope, 
- create transit gateways to connect account to aws network shared account
- transit gateway share
- create route53 forward and outbound resolver
- auto join AD for instances. it monitors new intsance creation with tags and joins them
- add stonebranch scheduler to ec2 instance with stone tag. looks similar to aws systems manager run command
- auto build ecr images from repository using codebuild. one codebuild for multiple images.
- remove default vpc
operation management
TFE bootstrap
customizations
aws organization linking (could just use control tower instead or account vending machine for account bootstrap)
- link to AWS Org
- install wiz and qualsys
- connect account to security hub
Accounts required
payer account to manage billing & OUs
one security account for each tools wiz, qradar (SIEM), AD domain controller.
Central DNS management account
Central network account that manages all transit. even to on-prem
3rd party transport account that allows you to connect to salesforce, SAP, mulesoft through VPN and private link
A shared service account??
