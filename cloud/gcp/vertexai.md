XGBoost training
For Vertex AI training jobs there are pre-built containers, including XGBoost: https://cloud.google.com/vertex-ai/docs/training/pre-built-containers#xgboost

The training code from the user can be supplied to the job in three ways:
https://cloud.google.com/vertex-ai/docs/training/code-requirements#choose_a_training_code_structure


supply a single .py script
create a python source distribution
copy the code to the pre-built container
If this is on the right track let me know if you would like example.  I have some in the same repo I provided earlier
ALSO, for large scale training I like Ray and Vertex AI has a Ray service that allows you to setup a Ray cluster, submit jobs (even with an SDK), and then shut the cluster down when done. 
https://cloud.google.com/vertex-ai/docs/open-source/ray-on-vertex-ai/overview
https://xgboost.readthedocs.io/en/stable/tutorials/ray.html




NVIDIA Triton Server Containers
There are OSS and hosted by Nvidia so they do need to be copied to GCP AR/GCR for use in Vertex AI.  
These come in 5 types that mostly reflect different combinations of backend.  The description of types can be reviewed at the following links.  By click on the tags tab you can also review the release history and see how frequently they are updated:
https://catalog.ngc.nvidia.com/orgs/nvidia/containers/tritonserver




For the other questions, are these still unanswered? Some brief thoughts follow:
The A100 ServiceUnavailable 503 Machine type temporarily unavailabe error looks like a stock out error - at that moment there were not enough A100 available in the region
for deploy time:
When a model registry is deployed it all stays avialble while a new deployment is in progress.  If you set max-replicas > min_replicas the endpoint continue to service request when new nodes are launched - just higher latency due to requests waiting their turn.  It might be helpful to set the min_replicas high enough to meet the regular demand, or choose a single node configuration that can handle the expected load so that scaling is not as crucial.  I know this can be hard with very spikey loads.
During a new deployment when a currently deployment is active it does create a new VM.  This means that the infrastructure is doubled until you undeploy the older version after shifting the traffic over to the new one.  This does give you the benefit of no downtime though.
https://github.com/statmike/vertex-ai-mlops/blob/main/05%20-%20TensorFlow/05Tools%20-%20Prediction%20-%20NVIDIA%20Triton.ipynb

https://github.com/triton-inference-server/fil_backend



