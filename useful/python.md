### How to install python3.12
Refer artical in https://techviewleo.com/how-to-install-python-on-amazon-linux-2/

#### Here are the commands
sudo yum update -y
sudo yum groupinstall "Development Tools" -y
sudo yum erase openssl-devel -y
sudo yum -y install wget yum-utils make gcc openssl11 openssl11-devel bzip2-devel libffi-devel zlib-devel
wget https://www.python.org/ftp/python/3.12.0/Python-3.12.0.tgz
tar xzf Python-3.12.0.tgz 
cd Python-3.12.0
sudo ./configure --enable-optimizations --prefix=/usr/local --enable-shared LDFLAGS="-Wl,-rpath /usr/local/lib"
sudo make -j ${nproc} 
sudo make altinstall 
sudo rm -f /bin/python3; sudo ln -s /usr/local/bin/python3.12 /bin/python3
sudo rm -f /usr/bin/python3; sudo ln -s /usr/local/bin/python3.12 /usr/bin/python3
sudo rm -f /usr/bin/pip3; sudo ln -s /usr/local/bin/pip3.12 /usr/bin/pip3

### Install AWS CDK
pip3 install aws-cdk-lib

### Create a new CDK app in python language
cdk init app --language=python

### Base64 decode
echo (text) | base64 --decode

###Zip a file to a folder and upload to S3
zip -r sagemaker.zip ./sagemaker/
aws s3 cp sagemaker.zip s3://devaws-gcp-s3-trigger-testing/sagemaker.zip

### Perform a inplace sort in linux
sort -o file{,}

### In Glue job, get python, dataproc, platform and architecture
import sys
import platform
print("Python Version:", sys.version)
print(
"Platform Architecture / System / Machine / Release: ",
platform.architecture()[0],
"/",
platform.system(),
"/",
platform.machine(),
"/",
platform.release(),
)

### Create Conda environment 
conda env create -y -f environment.yml

### Remove Conda environment 
conda remove -y --name triton_example --all

### Get Conda environments
conda env list

### Install Jupyter notebook
python -m ipykernel install --prefix "${DL_ANACONDA_HOME}" --name triton_example --display-name triton_example

### Install Anaconda with Python 3.10
mkdir -p ~/miniconda3
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O ~/miniconda3/miniconda.sh
bash /miniconda3/miniconda.sh -b -u -p /miniconda3
rm -rf ~/miniconda3/miniconda.sh
~/miniconda3/bin/conda init bash
~/miniconda3/bin/conda init zsh
source ~/.bashrc
conda update -y conda
conda create -y -n dataprocenv python=3.10
conda activate dataprocenv

### Build and run logstash using docker
docker build -t logstash .
docker run --rm -it logstash
docker run --rm -it us-central1-docker.pkg.dev/dnb-genai-gcp-sandbox-207616/samples/logstash
elasticsearch


### Git Credentials
git config --global credential. Helper store

### Display Tree of a directory
tree /f /a > tree.txt

### Check if python file has any error quickly
py -c "import PS_GFS_EquipmentPlay"
py -c "import py_compile;py_compile.compile('PS_Agilent_PS_IndirectTransactions_Attributes.py')"

### Kill all dccker container and free space
docker kill $(docker ps -aq)
docker rm $(docker ps -aq)
docker rmi -f $(docker images -aq)



### Generate RSA key
ssh-keygen -t rsa

### Generate latest public and private key
openssl genpkey -algorithm ed25519 -out private.pem
openssl pkey -in private.pem -pubout -out public.pem

### Install git on RHEL
dnf install -y git


### Upload triton image to GCR repository
TRITON_IMAGE="nvcr.io/nvidia/tritonserver:23.03-py3"
AR_IMAGE="us-east4-docker.pkg.dev/cc-revup-cc/triton/tritonserver:23.03-py3"
docker pull $TRITON_IMAGE
docker tag $TRITON_IMAGE $AR_IMAGE
gcloud auth configure-docker us-east4-docker.pkg.dev --quiet
docker push $AR_IMAGE


### To get all allowed Domains for a certificate 
openssl x509 -noout -text -in example-cc.cc.com.crt | grep DNS:

### Query ElasticSearch for custom indices
_cat/indices/*?v=true&s=index:desc



### Install mysql in rhel8
rpm --import https://repo.mysql.com/RPM-GPG-KEY-mysql-2023
dnf -y install mysql mysql-server


### Check MySQL DB Connections
mysql --ssl-ca=/etc/pki/tls/certs/server-ca.pem --ssl-cert=/etc/pki/tls/certs/client-cert.pem --ssl-key=/etc/pki/tls/certs/client-key.pem -u appuser -pXxxx@1234 -h 10.105.999.91 dbname

### Get client and server ca certificates from GCP Cloud SQL
gcloud sql ssl client-certs describe insight-dev --instance=abcd --format="value(cert)" > client-cert.pem
gcloud beta sql ssl server-ca-certs list --format="value(cert)" --instance=test-dev > ca.pem

### Troubleshooting cloud proxy using netstat
netstat -anp | grep -i 1234
ps -ef | grep -i 1234
kill -9 

### Run Cloud SQL Proxy in background
nohup ./cloud-sql-proxy --address 0.0.0.0 --port 1234 --private-ip nprd-revup-connect-devd9154a98:us-east4:lpi-dev &



### Install openssh on windows vm
https://learn.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse?tabs=powershell#install-openssh-for-windows


# Shutdown an linux machine now
shutdown -h now


### Check if Django app address alredy in use
fuser -k 8000/tcp
netstat -ntlp

### Fix for ssh unauthenticated WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED! in MOBAXTERM.
ssh-keygen -R 10.106.109.6

### Httpd permissions on Django App, start stop httpd, check httpd error logs
chmod -R 755 /var/www/html/ccc/
chmod -R 755 /var/www/html/ss_ccc_core/
systemctl stop httpd
systemctl start httpd
tail -fn10 /etc/httpd/logs/access_log
tail -fn10 /etc/httpd/logs/error_log

### Provide write permissions to everyone on a folder
chmod ugo+rwx -R /data



### Search content within a file in linux using grep 
grep -Rnw . -e 'Aws\Creden' -r

### Find commands to find files with names
find . -iname "elas*"

### Grep command to display lines above and beoow the matching text
ll -R | grep -20 -20 ProviderRepository.php


### Install mod_wsgi for 2.7 and httpd
wget https://github.com/GrahamDumpleton/mod_wsgi/archive/refs/tags/4.9.4.tar.gz
tar xvfz 4.9.4.tar.gz
cd mod_wsgi-4.9.4
./configure
rm -rf /bin/python; ln -s /bin/python2 /bin/python
cp /usr/lib64/httpd/modules/mod_wsgi.so /etc/httpd/conf.modules.d

### How to make a soap call
curl -X GET -H "Content-Type: text/xml" --data-binary @request.xml  https://testurl.com

### Reset Beyond compare to start trail version
reg delete "HKCU\Software\Scooter Software\Beyond Compare 4" /v CacheID /f

#### MSSQL Server running queries
select
P.spid
, right(convert(varchar, 
dateadd(ms, datediff(ms, P.last_batch, getdate()), '1900-01-01'), 
121), 12) as 'batch_duration'
, P.program_name
, P.hostname
, P.loginame
from master.dbo.sysprocesses P
where P.spid > 50
and P.status not in ('background', 'sleeping')
and P.cmd not in ('AWAITING COMMAND'
,'MIRROR HANDLER'
,'LAZY WRITER'
,'CHECKPOINT SLEEP'
,'RA MANAGER')
order by batch_duration desc

### Get count of lines for a file using powershell
"abc_202407_0000000000.csv" |% {$n = $_; $c = 0; Get-Content -Path $_ -ReadCount 1000 |% { $c += $_.Count }; "$n; $c"}

### Get count of lines for all files in a folder using powershell
Get-ChildItem -File | ForEach-Object { Get-Content $_ | Measure-Object -Line | Select-Object -ExpandProperty Lines } | Measure-Object -Sum | Select-Object -ExpandProperty Sum

### Split a file into number of lines
split T08450_XXXXX_20240731T235932Z_001_001.txt -l 100000000

### Split a file into number of parts
split -n 3 index.txt

### DNS lookup in Chrome
chrome://net-internals/?#dns
