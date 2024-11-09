
APIs start with . Example GET / _cluster/health
GET _cat/nodes?v --> to get output in table format
to get all hidden / system indices use => cat/incides?v&expand _widcards=all
1 shard is created by default. if need to increase shard, use split api and to reduce, use shrink api
To get status of all shards, try /_cat/shards
Get a document -> GET /products/_doc/100
Update a document -> 


Add script to update field -> 




For bulk update, have the content-type as application/x-ndjson


Remove elasticsearch
sudo systemctl stop elasticsearch
sudo rm -rf /var/lib/elasticsearch/*
sudo rm -rf /var/log/elasticsearch/*
sudo rm -rf /etc/elasticsearch/*
rpm --erase elasticsearch-8.13.2-x86_64.rpm
rpm --reinstall elasticsearch-8.13.2-x86_64.rpm
