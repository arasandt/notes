#Gcloud Connection
gcloud config set project x-xx-gcp-xx-207616 
gcloud auth application-default login
gcloud auth login
gcloud auth application-default revoke
gcloud auth revoke dayalxx@xxx.com

GCloud Commands
gcloud functions add-invoker-policy-binding aws-gcp-storage-trigger --region="us-central1" --member="MEMBER_NAME"
gcloud projects add-iam-policy-binding $PROJECT_ID --member serviceAccount:$PROJECT_NUMBER-compute@developer.gserviceaccount.com --role roles/eventarc.eventReceiver
gcloud functions add-invoker-policy-binding aws-gcp-storage-trigger --region="us-central1" --member="serviceAccount:xx-compute@developer.gserviceaccount.com"
gcloud storage cp bootstrap-template.yaml gs://gcp-trigger-bucket-123456789/abc.txt
aws s3 cp bootstrap-template.yaml s3://devaws-gcp-s3-trigger-test/abc.txt
gcloud storage cp bootstrap-template.yaml gs://gcp-pubsub-trigger-bucket-123456789/abc.txt
aws s3 cp bootstrap-template.yaml s3://devaws-gcp-sns-trigger-testing/abc.txt
aws s3 rb s3://devaws-gcp-sns-trigger-testing --force
gcloud storage cp samplefile.csv gs://dynamodbtest

Model list and describe
gcloud ai models describe model_tenant1 --region=us-central1
gcloud ai models describe 5805806223727001600 --region=us-central1


workflow list gcloud 
gcloud dataproc workflow-templates describe formaltemplate --region=us-central1
Bigtable creation
gcloud bigtable instances tables create samplefile --instance=bigtable-dynamo --project=xx-genai-gcp-xx-207616 --column-families="userid,firstname,lastname,score" --splits="userid"

login into instancei n gcloud
gcloud compute ssh --zone "us-central1-a" "elasticsearch-bastion" --tunnel-through-iap --project "xx-genai-gcp-xx-207616"


upload to gcp artifact registry
gcloud auth configure-docker us-central1-docker.pkg.dev
docker tag logstash us-central1-docker.pkg.dev/xx-genai-gcp-xx-207616/samples/logstash
docker push us-central1-docker.pkg.dev/xx-genai-gcp-xx-207616/samples/logstash
gcloud auth print-access-token | docker login -u oauth2accesstoken --password-stdin https://us-central1-docker.pkg.dev/



create secret
echo -n "my super secret data" | gcloud secrets create my-secret --replication-policy="user-managed" --data-file=-
gcloud secrets create DB_CERTS --replication-policy="user-managed" --data-file=elasticsearch-ca.crt --locations=us-east4
gcloud get all compute imamges
gcloud compute images list

GCP Event notifications
gcloud storage buckets notifications list gs://xx-dev-etl-stitch
gcloud storage buckets notifications create gs://xx-testing-snowflake --event-types=OBJECT_FINALIZE --topic=ops_copy_xx_to_customer_bucket_topic
gsutil notification delete gs://xx-testing-customers
gcloud storage buckets create gs://xx-testing-etl-stitch --location=us-east4


Gcloud get instance IP address
gcloud compute instances describe linux-rhel8 --zone=us-east4-a --project=xx-xx-xxasdasd --format="value(networkInterfaces.networkIP)"

Connect to Cloud SQL using proxy
https://cloud.google.com/sql/docs/mysql/connect-auth-proxy#windows-64-bit

(nohup) cloud-sql-proxy.x64.exe --address 0.0.0.0 --port 1234 --private-ip xx-xx-project-devd9154a98:us-east4:xxx-encrypted-qa 


Get dataprod cluster ip and masternode
instanceName=$(gcloud dataproc clusters describe revup-hbase-migration --region=us-east4 --format="list(config.masterConfig.instanceNames)")
machineTypeUri=$(gcloud dataproc clusters describe revup-hbase-migration --region=us-east4 --format="value(config.masterConfig.machineTypeUri)")
zone=$(echo $machineTypeUri | cut -d '/' -f 9)
gcloud compute instances describe $instanceName --zone=$zone --format="value(networkInterfaces[0].networkIP)"

stop an instance in gcloud
gcloud compute instances stop cc-dev-41-jfjm --project=x-xx-iq-xx--zone=us-east4-c
gcloud compute instances delete cc-dev-41-kzr7 --project=x-xx-iq-xx--zone=us-east4-a --delete-disks=all
gcloud compute instance-groups managed abandon-instances avbcd-mig --instances=avbcd-czxc --region=us-east4
gcloud compute instance-groups managed recreate-instances avbcd-mig --instances=avbcd-r1ms --region=us-east4

#ssh into a compute engine
$mig="ss-xx-st-mig"
$region="us-east4"
$instance=gcloud compute instance-groups list-instances $mig --format="value(NAME)" --region=$region --limit=1
$zone=gcloud compute instance-groups list-instances $mig --format="value(ZONE)" --region=$region --limit=1
$ip=gcloud compute instances describe $instance --zone=$zone --format="value(networkInterfaces[0].networkIP)"
ssh -i C:\\Users\\xx\\Downloads\\ssh\\.ssh\\xx.pem username@$ip



startup script location
sudo journalctl -eu google-startup-scripts.service
sudo tail -fn 100 /var/log/messages | grep startup-script-url

BCP Format file
bcp [reference_data].[dbo].[esg_new] format nul -c -x -f esg_new.xml -t, 
bcp [reference_data].[dbo].[esg_new] format nul -c -x -f esg_new.xml -t, -U xx -P xx@1234 -S 10.105.xx.44
bcp [reference_data].[dbo].[Scots_173_new] format nul -c -x -f Scots_173_new.xml -t, -U xx -P xx@1234 -S 10.105.xx.44
gcloud storage cp D:\Scots\Scots.csv gs://iq-xxxx-internal-user-stg/
gcloud sql import csv ss-mssql-stg gs://iq-xx-internal-user-stg/Scots.csv --database=reference_data --table=Scots_173_new --quote="22" --escape="5C" --fields-terminated-by="2C" --lines-terminated-by="0A" --project=sampleproject

run a cloud scheduler job 
gcloud scheduler jobs run fxxxqueuepreprd --project projectid --location us-east4
gcloud scheduler jobs run Fxxxx_Kicxxf_HTTP --project projected --location us-east4
gcloud scheduler jobs update http FedEx_KickOff --schedule="/15 6-23  SEP *" --time-zone=UTC --location=us-east4 --project np

Flush queue / subscriptions
gcloud pubsub subscriptions seek eventarc-us-east4-xxx-proxxone-14-281647-sub-856 --time=$(date +%Y-%m-%dT%H:%M:%S)

#Big table query
select * from FedExCreditCheck where applyforcreditenhancedresult['applyforcreditenhancedresult'] = ''
get functions variables 
gcloud functions describe FedEx_KickOff --region=us-east4 --format="json(serviceConfig.environmentVariables)" --project prd-xxxx
gcloud functions describe FedEx_ProcessOne_14 --region=us-east4 --format="json(serviceConfig.environmentVariables)" --project prd-xxx
Delete bigtable rows
cbt -project my-project -instance my-instance lookup my-table $'\224\257\312W\365:\205d\333\2471\315\'
cbt -instance ss-bigtable deleteallrows FedExCreditCheck  
cbt -instance ss-bigtable deleteallrows FedExFileProcessStatus 


Bigquery
square bigquery 
gcloud config set project xx-ss-4d6
bq mk --location=us-east4 --dataset --description "Dataset for xApp" xx_info
CREATE OR REPLACE EXTERNAL TABLE xx_info.sxx_info
(
x STRING,
x STRING,
---
)
WITH PARTITION COLUMNS (
year INT64,
month INT64,
day INT64
)
OPTIONS (
format = 'JSON',
uris = ['gs://xx-qa-env/xx/*.json'],
hive_partition_uri_prefix = 'gs://xx-qa-env/xx/',
require_hive_partition_filter = true
)
CREATE OR REPLACE EXTERNAL TABLE xx_info.xx_info_nonpart
(
xx STRING,
xx STRING,
---
)
OPTIONS (
format = 'JSON',
uris = ['gs://xx-qa-env/translogs/*.json'],
require_hive_partition_filter = true
)
SELECT *
FROM xx_tran_info.xx_tran_info
WHERE year = 2024 AND month = 10 AND day = 16
AND customerreference=xxx
LIMIT 10;