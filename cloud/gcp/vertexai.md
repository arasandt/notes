XGBoost training
For Vertex AI training jobs there are pre-built containers, including XGBoost: https://apc01.safelinks.protection.outlook.com/?url=https%3A%2F%2Fcloud.google.com%2Fvertex-ai%2Fdocs%2Ftraining%2Fpre-built-containers%23xgboost&data=05%7C02%7Carasandt%40virtusa.com%7Ca805c27126714ac560d008dc31564911%7C0d85160c589944caacc8db1501b993b6%7C0%7C0%7C638439493897203077%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C0%7C%7C%7C&sdata=a8H4xur1yG1%2Be8QFoX8oecw8hVg2Q4t2Cbw9p7s7%2BWs%3D&reserved=0

The training code from the user can be supplied to the job in three ways:
https://apc01.safelinks.protection.outlook.com/?url=https%3A%2F%2Fcloud.google.com%2Fvertex-ai%2Fdocs%2Ftraining%2Fcode-requirements%23choose_a_training_code_structure&data=05%7C02%7Carasandt%40virtusa.com%7Ca805c27126714ac560d008dc31564911%7C0d85160c589944caacc8db1501b993b6%7C0%7C0%7C638439493897213244%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C0%7C%7C%7C&sdata=e2epXvRNZ2K%2BnrjLqzQbEVJHSmuu7kK8myy0g3Dp8Go%3D&reserved=0

supply a single .py script
create a python source distribution
copy the code to the pre-built container
If this is on the right track let me know if you would like example.  I have some in the same repo I provided earlier
ALSO, for large scale training I like Ray and Vertex AI has a Ray service that allows you to setup a Ray cluster, submit jobs (even with an SDK), and then shut the cluster down when done. 
https://apc01.safelinks.protection.outlook.com/?url=https%3A%2F%2Fcloud.google.com%2Fvertex-ai%2Fdocs%2Fopen-source%2Fray-on-vertex-ai%2Foverview&data=05%7C02%7Carasandt%40virtusa.com%7Ca805c27126714ac560d008dc31564911%7C0d85160c589944caacc8db1501b993b6%7C0%7C0%7C638439493897221018%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C0%7C%7C%7C&sdata=3c2xsRNzo%2BICcOX8L9Q2pEYCau8Pl7OZPY%2FitaJBO%2FY%3D&reserved=0

https://apc01.safelinks.protection.outlook.com/?url=https%3A%2F%2Fxgboost.readthedocs.io%2Fen%2Fstable%2Ftutorials%2Fray.html&data=05%7C02%7Carasandt%40virtusa.com%7Ca805c27126714ac560d008dc31564911%7C0d85160c589944caacc8db1501b993b6%7C0%7C0%7C638439493897227538%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C0%7C%7C%7C&sdata=wmmXWov2bQ%2FbH2OjIKqIAT52oFNnaSgTylZUc%2Bn%2BDfU%3D&reserved=0

NVIDIA Triton Server Containers
There are OSS and hosted by Nvidia so they do need to be copied to GCP AR/GCR for use in Vertex AI.  
These come in 5 types that mostly reflect different combinations of backend.  The description of types can be reviewed at the following links.  By click on the tags tab you can also review the release history and see how frequently they are updated:
https://apc01.safelinks.protection.outlook.com/?url=https%3A%2F%2Fcatalog.ngc.nvidia.com%2Forgs%2Fnvidia%2Fcontainers%2Ftritonserver&data=05%7C02%7Carasandt%40virtusa.com%7Ca805c27126714ac560d008dc31564911%7C0d85160c589944caacc8db1501b993b6%7C0%7C0%7C638439493897233235%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C0%7C%7C%7C&sdata=UCssky7u%2FbHxiAcwFhJLmXV4kAR8ZXs3%2FvUyV1cHYpw%3D&reserved=0



For the other questions, are these still unanswered? Some brief thoughts follow:
The A100 ServiceUnavailable 503 Machine type temporarily unavailabe error looks like a stock out error - at that moment there were not enough A100 available in the region
for deploy time:
When a model registry is deployed it all stays avialble while a new deployment is in progress.  If you set max-replicas > min_replicas the endpoint continue to service request when new nodes are launched - just higher latency due to requests waiting their turn.  It might be helpful to set the min_replicas high enough to meet the regular demand, or choose a single node configuration that can handle the expected load so that scaling is not as crucial.  I know this can be hard with very spikey loads.
During a new deployment when a currently deployment is active it does create a new VM.  This means that the infrastructure is doubled until you undeploy the older version after shifting the traffic over to the new one.  This does give you the benefit of no downtime though.
https://apc01.safelinks.protection.outlook.com/?url=https%3A%2F%2Fgithub.com%2Fstatmike%2Fvertex-ai-mlops%2Fblob%2Fmain%2F05%2520-%2520TensorFlow%2F05Tools%2520-%2520Prediction%2520-%2520NVIDIA%2520Triton.ipynb&data=05%7C02%7Carasandt%40virtusa.com%7Ca8fcab801a494d3d2b0508dc1b90bb3f%7C0d85160c589944caacc8db1501b993b6%7C0%7C0%7C638415555635180865%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C3000%7C%7C%7C&sdata=ybaC0dt%2FWBVtVIKr0O96W0txjEIXAwypQA9xVC%2BaHlM%3D&reserved=0

https://apc01.safelinks.protection.outlook.com/?url=https%3A%2F%2Fgithub.com%2Ftriton-inference-server%2Ffil_backend&data=05%7C02%7Carasandt%40virtusa.com%7Ca8fcab801a494d3d2b0508dc1b90bb3f%7C0d85160c589944caacc8db1501b993b6%7C0%7C0%7C638415555635190050%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C3000%7C%7C%7C&sdata=F5Zm%2FTpnpOzGwSFWW8NJ571c3V9ADMVEKz5IO9fYFn4%3D&reserved=0


