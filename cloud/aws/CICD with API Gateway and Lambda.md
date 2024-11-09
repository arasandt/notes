Hi Sathish –

Based on our discussion last week, here are the best practices I have listed. Some of them might be already in place and others might be overkill at this point. Please consider ones which you feel should apply.
A DevOps engineer will have their own blueprint on how to build an entire pipeline (from Dev to Prod). I attended one of the Cognizant DevOps session and they showed us a blueprint.

Organizations
1.    Implement AWS Organizations
2.    Separate accounts for Production, Staging and Development. Separate accounts allows to make best use of Lambda Free Tier.
3.    A separate security account and CI/CD account.
4.    (optional) A Logging account
5.    Enforce tagging to organize resources within the account.
6.    Use Cloud9 for Developers
7.    Beyond SAM, see if you want to use Serverless or Stackery.

Security & Logging
1.    Using the security account created, assign least privilege roles across member accounts for CloudFormation, Developers, Lambda, CodeBuild, CodePipeline etc. This is task zero.
2.    Before any code is pushed to source control, make sure all the sensitive information are either moved to SSM Parameter Store or Secrets Manager. If CloudFormation or Lambda needs the secret, they have to look up in SSM Parameter store. Additionally, sensitive information can be encrypted via KMS.
3.    Authenticate and Authorize the API call using IAM, Cognito or Lambda Authorizers. If we already have federated access, then Cognito should be used.
4.    Enable X-Ray on Lambda and API Gateway. This allows detailed tracing at additional cost.
5.    Build a CloudWatch Dashboard to monitor how Lambda & API Gateway is performing. Dashboard can also include custom metrics.
6.    Template IAM policies for Serverless are readily available so we don’t have to create policies from scratch. Ex: SQSPollerPolicy
7.    Firewall for API Gateway can be implemented using WAF (changes does not need re-deploy) or API Gateway resource policy (changes would need a re-deploy).
8.    Include a notification mechanism which aligns with Org structure.

Testing
1.    SAM provides a way to test API and Lambda locally. So make sure the tests pass locally before pushing code to AWS.
2.    Peer review using pull requests. No merge until reviewed.
3.    Validate templates locally as well as within CodePipeline.

Lambda & Deployment
1.    Build the “deployment preference” into the SAM template. They can be
-    Linear (safe deployment)
-    Canary (safe deployment)
-    All-at-once
Include CloudWatch alarms to monitor the failure and rollback if alarm is triggered. Similarly, you can build pre-traffic and post-traffic hooks using Lambda itself during shifting traffic. Don’t use canary or linear if there is a potential that data can be lost.
2.    Use aliases during new version deployment so that we don’t have to change APIs pointing to them.
3.    Logically groups http methods into a single lambda function. This makes sure Lambda uses memory allocated efficiently.
4.    Separate out business functionality into multiple functions / files or put them into layers to prevent code duplication.
5.    Interactions between Lambda should happen asynchronously using EventBridge (there are other ways too). However, because of the asynchronous nature, UI should be built accordingly.

CI/CD
1.    Use CodeCommit or GitHub for source control. Have buildspec.yml (if using CodeBuild) and requirements.txt in root.
2.    Use SAM template (template.yml) for creating and updating stacks.
3.    CodePipeline for sourcing, building, creating a change set, approving it and then executing it.
4.    For every commit, create a sub-folder in S3 bucket which will hold build artifacts related to that commit id. Nice way to segregate. This should be a pre-build step.
5.    A production-level pipeline moves across 3 accounts. DevOps person should have this blueprint.
6.    Code Coverage Tests as part of build. SonarCloud for Code Quality.
7.    (optional) Perform API testing using ReadyAPI or Runscope.
8.    Build IaC and Application Code separately and then finally merge it as final build artifact.
9.    Perform custom build with StepFunctions if required.

API Gateway
1.    Always use aliases to refer to Lambda functions.
2.    Use Route 53 for providing a custom domain name for APIs.
3.    Use stage variables to provide different values to same variables across stages.
4.    Enable CORS
5.    Throttling is available @account, @method, @client level. Make sure you provide required limits for each method so that critical APIs don’t fail. Create a usage plan per client if required.
6.    (optional) To prevent excessive call of lambda for malformed request, you can perform data modeling in API level itself.


Visited
Stage variable to save configurations setting for each stage. Stage variable allows you to give different values to same variable to be pointed (ex: alias) https://youtu.be/zJQDAsWm-5k?t=1606

Traffic shifting with aliases is called safe deployment. https://youtu.be/zJQDAsWm-5k?t=1733

In SAM there is SQSPollerPolicy temaplate which is an inbuilt policy for certain actions. This will cut down SAM code. If we attach this policy to function, it will provide all permissions necessary to poll a queue. https://github.com/aws/serverless-application-model/blob/develop/samtranslator/policy_templates_data/policy_templates.json

A production level pipeline  https://youtu.be/zJQDAsWm-5k?t=3192 and https://youtu.be/zJQDAsWm-5k?t=3233

For APITest  in Deploy-Staging use runscope tool https://www.runscope.com/

AWS came up with Create Application, which will give us a SAM template and also do a Ci/CD pipeline. But not available for python.
There are two types of build you can do. Try IaC build and then Application Code Build. IaC build can have SAM template and common templates like CW alarms for new lambda.
Use HTTP API vs REST API if you want to use API Gateway just to call Lambda. Because API Gateway is powerful and thus costs more if you use REST API than HTTP API.
Lambda should be coded as, 1. Dependencies, handler, common helper functions (connect to DB, get parms from parameter store) and business logic sub-functions. Separate business logic from handler functions. If duplicity, then use layers.
Do data modelling at the API level. Even use regex. Validating here make sure lambda is not called. We can use mapping template to change schema
IF lambda is not going to transform but just used to transfer, then directly integrate with the service but again you have to define a mapping template.
