install python3.12
https://techviewleo.com/how-to-install-python-on-amazon-linux-2/


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
pip3 install aws-cdk-lib
cdk init app --language=python

#base64 decode
echo dGVzdGluZzEyMw== | base64 --decode


#Zip a file
zip -r sagemaker.zip ./sagemaker/
aws s3 cp sagemaker.zip s3://devaws-gcp-s3-trigger-testing/sagemaker.zip

inplace sort in linux
sort -o file{,}


Glue job python dataproc platform architecture
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
add conda environment to notebook
install it in base
conda env create -y -f environment.yml
conda remove -y --name triton_example --all
conda install -y --channel "rapidsai" --channel "nvidia" cuml=23.12 cudf=23.12
conda env list
python -m ipykernel install --prefix "${DL_ANACONDA_HOME}" --name triton_example --display-name triton_example

Anaconda install6
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


Docker logstash
docker build -t logstash .
docker run --rm -it logstash
docker run --rm -it us-central1-docker.pkg.dev/dnb-genai-gcp-sandbox-207616/samples/logstash
elasticsearch
export ELASTIC_PASSWORD=""


1AJIPV6A0KaPYETLqFeVF_OwHg4NJWEvfdabn3zwHQUWbafQ1qkOd5SridQgil551HZGXE2P76CwIJhIO
cd deepracer-for-cloud/ && source bin/activate.sh && dr-stop-training
dr-upload-custom-files && dr-start-training

git credentials
git config --global credential. Helper store

Display Tree of a directory
tree /f /a > tree.txt

check if python file ahs any error
py -c "import PS_GFS_EquipmentPlay"
py -c "import py_compile;py_compile.compile('PS_Agilent_PS_IndirectTransactions_Attributes.py')"

Kill all container and make space
docker kill $(docker ps -aq)
docker rm $(docker ps -aq)
docker rmi -f $(docker images -aq)



Generate RSA key
ssh-keygen -t rsa
install git on RHEL
dnf install -y git


UPload triton image
TRITON_IMAGE="nvcr.io/nvidia/tritonserver:23.03-py3"
TRITON_IMAGE="hello-world"
AR_IMAGE="us-east4-docker.pkg.dev/cc-revup-cc/triton/tritonserver:23.03-py3"
docker pull $TRITON_IMAGE
docker tag $TRITON_IMAGE $AR_IMAGE
gcloud auth configure-docker us-east4-docker.pkg.dev --quiet
docker push $AR_IMAGE

Generate latest pub/private key
openssl genpkey -algorithm ed25519 -out private.pem
openssl pkey -in private.pem -pubout -out public.pem

To get allowed DNS for a certs 
openssl x509 -noout -text -in example-cc.cc.com.crt | grep DNS:

Elastic Search query custom indices
_cat/indices/*?v=true&s=index:desc



install mysql in rhel8
rpm --import https://repo.mysql.com/RPM-GPG-KEY-mysql-2023

dnf -y install mysql mysql-server


#DB Connections
mysql --ssl-ca=/etc/pki/tls/certs/server-ca.pem --ssl-cert=/etc/pki/tls/certs/client-cert.pem --ssl-key=/etc/pki/tls/certs/client-key.pem -u appuser -pXxxx@1234 -h 10.105.999.91 dbname

Get cert name
gcloud sql ssl client-certs describe insight-dev --instance=abcd --format="value(cert)" > client-cert.pem
gcloud beta sql ssl server-ca-certs list --format="value(cert)" --instance=test-dev > ca.pem

#troubleshooting cloud proxy
netstat -anp | grep -i 1234
ps -ef | grep -i 1234
nohup ./cloud-sql-proxy --address 0.0.0.0 --port 1234 --private-ip nprd-revup-connect-devd9154a98:us-east4:lpi-dev &
kill -9 
ip a


Install openssh on windows vm
https://learn.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse?tabs=powershell#install-openssh-for-windows


shutdown an linux machine
shutdown -h now


django address alredy in use
fuser -k 8000/tcp
netstat -ntlp

fix for ssh unauthenticated WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED! 
ssh-keygen -R 10.106.109.6

httpd permissionsa and httpd error logs
chmod -R 755 /var/www/html/ccc/
chmod -R 755 /var/www/html/ss_ccc_core/
systemctl stop httpd
systemctl start httpd
tail -fn10 /etc/httpd/logs/access_log
tail -fn10 /etc/httpd/logs/error_log

provide write permissiosn to everyone
chmod ugo+rwx -R /data


search content within a file in linux using grep. find files with names
grep -Rnw . -e 'Aws\Creden' -r
find . -iname "elas*"
grep below and above 
ll -R | grep -20 -20 ProviderRepository.php

mod_wsgi for 2.7 and httpd
wget https://github.com/GrahamDumpleton/mod_wsgi/archive/refs/tags/4.9.4.tar.gz

tar xvfz 4.9.4.tar.gz
cd mod_wsgi-4.9.4
./configure
rm -rf /bin/python; ln -s /bin/python2 /bin/python
cp /usr/lib64/httpd/modules/mod_wsgi.so /etc/httpd/conf.modules.d

how to make a soap call
curl -X GET -H "Content-Type: text/xml" --data-binary @request.xml  https://testurl.com

reset Beyond compare
reg delete "HKCU\Software\Scooter Software\Beyond Compare 4" /v CacheID /f

MSSQL Server runnign queries
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

get count of lines
"abc_202407_0000000000.csv" |% {$n = $_; $c = 0; Get-Content -Path $_ -ReadCount 1000 |% { $c += $_.Count }; "$n; $c"}
Get-ChildItem -File | ForEach-Object { Get-Content $_ | Measure-Object -Line | Select-Object -ExpandProperty Lines } | Measure-Object -Sum | Select-Object -ExpandProperty Sum

Split ELI file
split T08450_XXXXX_20240731T235932Z_001_001.txt -l 100000000
or split -n 3 index.txt

DNS lookup 
chrome://net-internals/?#dns
