# GCP Reference

## GKE

- A managed kubernetes service provided by gcp.
- Provides pod autoscaling
- Cluster autoscaling
- Cloud Logging and Cloud Monitoring can be easily enabled.
- GKE uses Container optimized OS
- Persistent disk and local disk can be mounted to pods.

Creating a cluster

```shell
gcloud container clusters create
```

Standard:

- Creating node pools and managing node is customer responsibility

Autopilot:

- Management is up to gke

```shell
    gcloud config set project my-kubernetes-project-304910
    gcloud container clusters get-credentials my-cluster --zone us-central1-c --project my-kubernetes-project-304910
    kubectl create deployment hello-world-rest-api --image=myrepo/hello-world-rest-api:0.0.1.RELEASE
    kubectl get deployment
    kubectl expose deployment hello-world-rest-api --type=LoadBalancer --port=8080
    kubectl get services
    kubectl get services --watch
    curl 35.184.204.214:8080/hello-world
    kubectl scale deployment hello-world-rest-api --replicas=3
    gcloud container clusters resize my-cluster --node-pool default-pool --num-nodes=2 --zone=us-central1-c
    kubectl autoscale deployment hello-world-rest-api --max=4 --cpu-percent=70
    kubectl get hpa
```

- To get credentials of a cluster

```shell
gcloud container clusters get-credentials cluster-name
```

## Cloud Function

Small function which can be added and up in production in very less time.
Cloud functions are event driven as well. 

## Cloud Run

zero to production in seconds for containers.

## Anthos

When nodes are multi-cloud, cloud or on prem, Anthos can be used.

## Different types of storage in GCP

Block storage:
A storage like hard-disk. One block storage  can be attached to one server.
A number of block storage devices can be attached to a single serve.

File Storage:
Shared across many servers.