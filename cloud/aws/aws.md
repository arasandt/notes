aws s3api put-bucket-logging --bucket aws-gcp-destination-testing --bucket-logging-status file://logging.json
aws s3api put-bucket-logging --bucket devaws-gcp-ai-ml-common --bucket-logging-status="{}"
aws s3api put-bucket-versioning --bucket devaws-gcp-sns-trigger-test --versioning-configuration="{\"Status\":\"Suspended\"}"
YOUR_BUCKET="devaws-gcp-s3-trigger-testing"
aws s3api delete-objects --bucket ${YOUR_BUCKET} --delete "$(aws s3api list-object-versions --bucket ${YOUR_BUCKET} --query='{Objects: DeleteMarkers[].{Key:Key,VersionId:VersionId}}')"


aws sts get-access-key-info --access-key-id AIDAR3MO2UCKFWE3EO4ZI

aws start sessions
aws ssm start-session --target i-0e5ca89799d7712c1
copy over deepracer
aws s3 cp s3://aws-gcp-sagemaker-models/rf7hills-1 s3://elasticbeanstalk-us-east-1-152706161531/rf7hills-1 --recursive --acl bucket-owner-full-control

http://10.104.146.175/lab/tree/Training_analysis_custom.ipynb



Cloud Trail querying in athena
https://docs.aws.amazon.com/athena/latest/ug/cloudtrail-logs.html#create-cloudtrail-table-org-wide-trail

ALTER TABLE cloudtrail_logs ADD
PARTITION (region='us-east-1',
year='2024',
month='07',
day='04')
LOCATION 's3://aws-cloudtrail-logs-127537946772-625c5396/AWSLogs/127537946772/CloudTrail/us-east-1/2024/07/04/'
SELECT * FROM "data_catalog_db"."cloudtrail_logs" where eventname = 'RunInstances';
https://www.gorillastack.com/blog/real-time-events/cloudtrail-event-names/#ec2-cloudtrail

This is sample .aws/config file for single signon
[profile testprod]
sso_start_url = https://d-xxxxxx.awsapps.com/start#
sso_region = us-east-1
sso_account_id = 1588xxxxx770
sso_role_name = xxl_prod_rxxonly
region = us-east-1
output = json


[default]
region = us-east-1
output = json




SSO Login
aws sso login --profile vizdev

