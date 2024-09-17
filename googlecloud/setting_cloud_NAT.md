I was unable to download notebook from Github using wget.
```sh
wget https://raw.githubusercontent.com/GoogleCloudPlatform/vertex-ai-samples/main/notebooks/community/model_garden/model_garden_pytorch_owlvit.ipynb
```
Even curl failed.
```sh
curl -I https://raw.githubusercontent.com/
```


Following the instruction from ChatGPT, I created a firewall rule to allow HTTP and HTTPS traffic, using the below command.
```sh
gcloud compute firewall-rules create allow-http-https \
    --network my-vpc-network-v1 \
    --allow tcp:80,tcp:443 \
    --direction=EGRESS
```

Later I found out that if the VM is in a private VPC subnet, you need to create a NAT gateway for the VM to access the internet.
```sh
gcloud compute routers nats list --network my-vpc-network-v1
```

```sh
gcloud compute routers create my-vpc-network-v1-router --network my-vpc-network-v1 --region us-central1
gcloud compute routers nats create my-vpc-network-v1-nat \
    --router=my-vpc-network-v1-router \
    --nat-all-subnet-ip-ranges \
    --auto-allocate-nat-external-ips \
    --region=us-central1
```

Post these changes, I was able to download the notebook using wget.