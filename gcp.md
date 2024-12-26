# Google Cloud Platform (GCP) Cheatsheet for DevOps Beginners

## Table of Contents
- [Basic Commands](#basic-commands)
- [Compute Engine](#compute-engine) 
- [Cloud Storage](#cloud-storage)
- [Kubernetes Engine (GKE)](#kubernetes-engine)
- [Cloud Functions](#cloud-functions)
- [IAM & Security](#iam--security)
- [Networking](#networking)

## Basic Commands

### gcloud CLI Installation & Auth
```bash
# Install gcloud CLI
curl https://sdk.cloud.google.com | bash

# Initialize gcloud
gcloud init

# Authenticate
gcloud auth login

# Set project
gcloud config set project PROJECT_ID

# List configurations
gcloud config list

```
# Compute Engine
### VM Instance Management
```
# Create VM instance
gcloud compute instances create INSTANCE_NAME \
    --machine-type=e2-medium \
    --zone=us-central1-a \
    --image-family=debian-10 \
    --image-project=debian-cloud

# List instances
gcloud compute instances list

# SSH into instance
gcloud compute ssh INSTANCE_NAME --zone=ZONE

# Stop instance
gcloud compute instances stop INSTANCE_NAME --zone=ZONE

# Start instance
gcloud compute instances start INSTANCE_NAME --zone=ZONE

# Delete instance
gcloud compute instances delete INSTANCE_NAME --zone=ZONE

```
# Cloud Storage
## Bucket Operations
```
# Create bucket
gsutil mb gs://BUCKET_NAME

# List buckets
gsutil ls

# Copy files to bucket
gsutil cp LOCAL_FILE gs://BUCKET_NAME/

# Download from bucket
gsutil cp gs://BUCKET_NAME/FILE LOCAL_PATH

# Delete bucket
gsutil rb gs://BUCKET_NAME

```

# Kubernetes Engine
## CLuster Operations

```
# Create cluster
gcloud container clusters create CLUSTER_NAME \
    --num-nodes=3 \
    --zone=us-central1-a

# Get credentials
gcloud container clusters get-credentials CLUSTER_NAME \
    --zone=us-central1-a

# List clusters
gcloud container clusters list

# Delete cluster
gcloud container clusters delete CLUSTER_NAME --zone=ZONE

```

# Deployment Operations

```
# Deploy application
kubectl create deployment APP_NAME --image=IMAGE_NAME

# Expose deployment
kubectl expose deployment APP_NAME --type LoadBalancer --port 80

# Scale deployment
kubectl scale deployment APP_NAME --replicas=3

# Get pods
kubectl get pods

```

# Cloud Functions

### Function Management

```
# Deploy function
gcloud functions deploy FUNCTION_NAME \
    --runtime python39 \
    --trigger-http \
    --entry-point function_name

# List functions
gcloud functions list

# Delete function
gcloud functions delete FUNCTION_NAME

# Get logs
gcloud functions logs read FUNCTION_NAME

```