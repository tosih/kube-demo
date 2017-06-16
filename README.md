## Setup Kubernetes

* Add Hosted Zone in AWS
* Add NS Records in domain DNS settings for AWS nameservers
* Create Cluster (w/ kops)
```$ kops create cluster --name=k8s.tosih.org --state=s3://<s3_bucket_name> --zones=us-west-1a --node-count=3 --node-size=t2.micro --master-size=t2.micro --vpc=<vpc_id>```
```$ kops update cluster k8s.tosih.org --yes```
* Validate Cluster
```$ kops validate cluster```

## Deploy application
```$ kubectl apply -f -R k8s

## Try app out!