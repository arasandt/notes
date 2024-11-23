Cloud Center of Excellence 
Consists of  
AWS Infra Engineers 
Security Engineers 
Application Engineers 
Operation Engineers 
Lead Architect 

Assess Phase 
Migration Evaluator 
Migration Readiness Assessment  
Migration Hub 

Mobilize 
Know about 7Rs 
Create a Landing Zone 
Organization Account 
Security Account 
Shared Services Account 
Log Archive Account 

Ultimately, create an account vending machine / AWS Control Tower 
For DB migration, there are database migration playbooks and reference guides 


Create 7Rs swim lanes for the application suite that needs to be migrated. 
Enable Metered Billing  
For Java Migration, use github.com/windup 
Follow 12 Factor App methods. Externalize Sessions so that you can scale properly.  
 
 
 
 
 
 
 
 
 
 
 
Use AppDynamics to view application dependencies 
Tight Monitoring 
Rehost and Optimize is a powerful combo 
Cleanup resources as you go 
For database migration, remove the code out of the db like PL/SQL. 
Create a data perimeter. Only trusted identities accessing trusted resources from trusted networks. 
Control data access / perimeter using path based roles. Easier to manage. Ex: role/universal/DEVELOPER 
Always check for quotas and supported region before create multiple instances of the resources in different namespaces. There is a region limit and account limits.  
 
 
Relocate – VMware Cloud on AWS 
Rehost – AWS Migration Service (MGN) rebranded from CloudEndure. Use CloudEndure Migration Factory (CEMF) to automate migration in waves. 
Replatform – DMS, Docker, K8s 
Refactor – Use Migration Hub Refactor Spaces 
 
 
 
When CDC pipelines are not moving much data, then it means that all the writes are already sync’d up to the new database through the dual write proxy layer. Mainframe RDBMS no longer needed as gold source. 
 
 
Migration Workshop 
https://catalog.us-east-1.prod.workshops.aws/workshops/a033522c-f256-40f9-9ecb-5b76a71589bc/en-US 
 
 
Automated Server Data Import Process à Wave Planning will run a terraform script for the servers, to create SGs or Firewalls. Then a Lambda will validate it and then import the servers into Migration Factory. 
 
 
CloudEndure Migration Factory can be installed in one account to perform migration in multiple accounts. 
 
