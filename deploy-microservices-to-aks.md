# Deploy Microservices to AKS

A Kubernetes cluster (AKS) has been created for you

Everyone has one AKS Namespace allocated

Adjust this script to set your
- User Id (Example:niyo1)
- Namespace (Example:niyo1-ns)

```bash
MY_USERID=niyo1
```

Run this script line by line to deploy microservices to your namespace

```bash
# setup environment
TENANT=7e6aac94-cc04-4004-b33a-270d4bf20d66
RESOURCE_GROUP=NiyoBootcampAdmin
AKS_CLUSTER_NAME=aksworkshop-142
MY_NAMESPACE=$MY_USERID-ns
alias k=kubectl
```
```bash
# after setup, run the following commands to deploy microservices
az login --tenant $TENANT

az aks get-credentials -g $RESOURCE_GROUP --name $AKS_CLUSTER_NAME

git clone https://github.com/Azure-Samples/azure-voting-app-redis.git

cd azure-voting-app-redis

k config set-context --current --namespace=$MY_NAMESPACE

k describe roles
k describe rolebindings

k apply -f azure-vote-all-in-one-redis.yaml

k get pods -w 
k get services -w

# open a browser and browse the Service External IP 

# goto Azure Portal and view namespace, pods and services
```
