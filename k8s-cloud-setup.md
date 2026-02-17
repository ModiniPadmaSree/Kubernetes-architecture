Kubernetes Cluster Setup on Cloud Platforms \

Kubernetes clusters can be deployed on major cloud platforms using managed services. \
1. AWS – Amazon EKS

Using Amazon EKS (Elastic Kubernetes Service) \

Amazon EKS is a managed Kubernetes service provided by AWS. The control plane is fully managed by AWS. \

Steps to Set Up EKS Cluster:

- Install AWS CLI and configure credentials. \
aws configure
- Install eksctl (CLI tool for EKS).
- Create IAM roles
- Create cluster using eksctl. \
eksctl create cluster \
  --name my-cluster \
  --region us-east-1 \
  --nodegroup-name worker-nodes \
  --node-type t3.medium \
  --nodes 2

- Update kubeconfig.

- Verify nodes are running. \
kubectl get nodes
2. Azure – Azure Kubernetes Service (AKS) \

Using Azure Kubernetes Service (AKS) \
AKS is Microsoft’s managed Kubernetes service. \

Steps:

- Login using Azure CLI. \
az login

- Create resource group. \
az group create \
  --name myResourceGroup \
  --location eastus

- Create AKS cluster. \
az aks create \
  --resource-group myResourceGroup \
  --name myAKSCluster \
  --node-count 2 \
  --enable-managed-identity \
  --generate-ssh-keys


- Connect cluster to kubectl. \
az aks get-credentials \
  --resource-group myResourceGroup \
  --name myAKSCluster


- Verify node status. \
kubectl get nodes \
In AKS: \

Control plane is managed by Azure. \

Node pools are created as virtual machines. \
3. Google Cloud – Google Kubernetes Engine (GKE) \

Using Google Kubernetes Engine (GKE) \

GKE is Google Cloud’s managed Kubernetes service. \

Steps:

- Install and configure gcloud CLI. \
gcloud auth login

- Enable Kubernetes Engine API. \
gcloud services enable container.googleapis.com


- Create GKE cluster. \
gcloud container clusters create my-cluster \
  --num-nodes=2 \
  --zone us-central1-a
- Configure kubectl credentials. \
gcloud container clusters get-credentials my-cluster \
  --zone us-central1-a


- Verify cluster nodes. \
kubectl get nodes

In GKE: \

Control plane is managed by Google. \

Worker nodes are created as Compute Engine instances.
