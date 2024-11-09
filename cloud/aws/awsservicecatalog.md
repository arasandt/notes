Management account can also used to provision roles. It depends on what we want to do.  We can use management account so that when an account is added, the roles are automatically created or  we need get into the member account and create roles ourselves
Metrics from SC usage. Help to know if somebody is really using a version or not
Have to see if portfolio sharing between from hub to spoke accounts required some extra permissions or not.
Daily report of provisioned reports within a portfolio to the owner based on tags.
Within product we can have version for windows as well as linux
How to look at all outputs. No place other than Service Catalog
Unless the roles are created in the member account, the sharing will not work. Roles are required for sharing to work since the role is embedded I guess.
When sharing with Organization the portfolio will automatically show up in the member account but if we share with account then the account has to import it.
Service actions can be even more complex which can take different inputs from user and then based on that the action can vary a little. But must maintain an audit record. But standardization is key here. Should we even do this.
If every service action needs a notification, then we have to customize it with a lambda instead of SSM templates. This is apart from the inbuild notification that SC provides.
Based on who is requesting it, we can limit the options that comes in dropdown of service catalog based on portfolio or tag values. Catalog can be deployed into individual accounts instead of importing. May be do this if Hub account option is not feasible. When you import the service catalog, you do not add users or tag options. But after its imported, then you run another stack that will populate this Based on which LOB it is.
While provisioning products a new key value can also be added. So based on this tag the role can have access to only those tagged resources. Not sure if this can be done.
Looks like product should be itself in different repo or folder so that app dev can focus on creating products and not worry about deploying service catalog.
Report on which account uses which version of a product so that we can nudge them to start using the new version. Visibility on what is being deployed.
Turn off instances during non business hours to save cost or just weekends
AWS Serverless Application Repository. Look at this.
Customer DNS request for routing to api gateways with SC products
The product should follow application patterns where developers can come and choose the pattern they wanted to follow. Select an deploy it.
By looking at the all account web page looks like accounts are provisioned via control tower
Create quicksight dashboard to view SC usage. Refer youtube.
Since Terraform Enterprise Udeploy is there, there cannot be a self-service for CI/CD.
Add a tag to tell who exactly from the role provisioned it
Not sure if VPC should be selectable
Enable Scheduled deletion of stack
A product can be made invisible if it’s been used for specified number of times. Refer youtube “track and manage product usage with AWS SC”. This sends notification and reports too. Definitely worth checking.
Can we let the user launch the GPU instance but then we can shut it down because its not allowed for the BU. Use AWS Config for that. Or you can use a different template constraint for the same product and that can also limit.
Any software from marketplace can be imported into service catalog.
Update of the same version of the provisioned product which create a change set and deploy.
Service action can be added later to the production version which would be visible to the provisioned product too
Create ephemeral resources via SC for a period.
Check how to deactivate older versions
Create view or help document on how to use the product
Group Configuration by Service Lines and configuration in its each folder
How to know whether to deploy ec2 instance in private subnet
What if different groups need different types of EC2 instance. How to control that? Template constraint usually does that.
How to handle security patches are ec2 creation.
Not sure if there is dynamodb or bastion host Use case
Single SSO mapping to Launch Role that the end user will be using. End the user roles should also have access to the S3 nbucket
AD group mapping to role should be managed by the user. Find out how to do it.


From CF, create a lambda function that will run a Jenkins pipe that will execute a terraform. – One example of integration. When a product is requested, a Jenkins pipeline runs that will execute terraform to deploy (OR) Terraform opensource configuration files in Service Catalog for resource provisioning. Deploy Terraform Open Source Engine as SQS, EC2 instance, Step Functions etc.


 
 
***************************
Add load balancer to ec2
Catalog can also create ECR images so that products can use it. This is like base installation.
Make sure every update to SC input fields / parameter works and does not fail the stack.
Design pattern is that the imported portfolio is looked at and then local portfolio is created by local admins by changing it a little. There may or may not be a feedback loop to main catalog admins.
AutoTags contain provisioning principal, so we know who is provisioning.
Builders can use the service catalog product as nested stack in their own template. Also we can take outputs of one SC product and pass as parameter to another SC Product.
By using app registry, I can get the cost at the application level (not just product or portfolio level)
 

 


Find out exact use cases. Do we need AMIs or EC2 or a simple solution?
Use Hub and Spoke Model for deployment. Centralized Hub enabled on-click deployment of updates.
Use AWS CF Stacksets and AWS Organizations
Apply Automated Tagging
Security Based into curated AMIs for EC2
EC2 automatic domain join
Least Privileged access
Target the Stackset for a OU / LOB. The moment an account is dropped into a OU, then stackset runs and creates the Service Catalog portfolio
Usually 4 sets of portfolios


Developer will not have access to provision resources in Dev account. Only from Service Catalog they would be able to do.
Each product within the portfolio should have a launch role. User can manage the EC2 instance using Service Actions (using SSM automation documents) which would also use the launch role.
There are 2 type of constraints, Template and Launch constraint
We can set-up tagoptions library with which I can setup Product, portfolio and account level tags.
Also add budgets always
Do we need Service Now or Jira Integration for intake?
How to grant users access to the portfolio? I think its should be handled via Role.
Multi-Account / Multi-region à From management account, create stacksetexecutionrole with a trust policy on the member account. Also deploy enduser (to use Service Catalog) roles and launch roles. Once you share the catalog, then you can add tagoptions and users in the member account by using stackset


To share Product with OU you will need OU ID. A member account must import the portfolio too.
We can also do product chaining.

 
 
