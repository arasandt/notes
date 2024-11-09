Below are few learnings
Backup Activity Impact: Performance is significantly impacted during Cloud SQL backup activity. Therefore, time-critical loads should be performed outside of maintenance windows. Additionally, simultaneous queries running on the database may also lead to execution delays. Note that in AWS, no backup activity is performed on the DB.
BCP Mechanics:
BCP uploads data to DB transaction logs before moving it sequentially to tables. This increases throughput during data transfer.
BCP does not support quoted fields in CSV file. Therefore, to load quoted CSV fields, it is necessary to first transform them using Python Pandas. This may result in increased loading times, but can be offset by implementing parallel loads.
CPU Core Limitation: The number of concurrent processes, to achieve maximum efficiency, is limited by CPU cores (e.g., for an 8 vCPU setup, I can execute up to 8 processes concurrently). Additionally, aligning this with the number of file chunks will enhance overall performance.
Multi-threading vs Multi-processing: The transformation of CSV files using multi-threading did not yield any performance improvements compared to a sequential approach. Thus, I switched to multi-processing to enhance performance. The implementation of BCP parallelism with multi-threading met expectations, so I did not pursue multiprocessing for this component.
Concurrency Complexity: The implementation of concurrency introduces a level of complexity. When concurrent jobs fail after the maximum number of retries, manual intervention (to re-run the failed load) is required, if a full re-run is not feasible. Additionally, the code required to manage concurrency and retries has become complex.

This is response from GCP
1.  60 GB file location: Where is the 60GB file located in relation to your SQL Server instance in each environment?If the source file for bcp is located on a different server or network than the sql server instance, network latency can affect performance. 
 
2. SQL Server CPU and memory:  Are those SQL Server instances comparable in terms of CPU, memory, and disk I/O performance? 
 
3. Disk IO: The bcp utility relies heavily on disk I/O, both for reading the source file and writing to the database. Check disk I/O utilization during the load process.
 
4. SQL Server configurations / parameters: Are both SQL Servers running the same versions and edition? are there any differences in the configurations ( memory settings, max degree parallelism, cost threshold for parallelism etc)
 
5.  Database settings: Do both of  DB have the same settings such as recovery models (simple vs bulk logged) and index fragmentations?
 
6. Database lock contentions/ other queries: Were both of them under the same load? were there any queries running/ creating any lock contentions during the bcp ?
 
7. Other bcp specific factors:  such as command line options  -c vs -n mode , format files, batching that can overall impact the performance of the bcp as Jimmy suggested. 
https://learn.microsoft.com/en-us/sql/tools/bcp-utility?view=sql-server-ver16&tabs=linux#-b-batch_size

