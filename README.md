______________________________________________________________________

<div align="center">

# EMLO Session 16 - Kubernetes I

</div>

# Description
In this repo, we deploy a CLIP model with a FASTAPI backend on a local Kubernetes cluster using [Minikube](https://github.com/kubernetes/minikube) exposed as a service using the Kubernetes Ingress Controller

# Installation
Install the following tools

[Docker](https://docs.docker.com/engine/install/)

[Minikube](https://minikube.sigs.k8s.io/docs/start/)

- For Linux
```
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube
```

- For Mac
```
brew install minikube
```

- For Windows
```
winget install minikube
```

# Build and Load Docker Image into Minikube

## Start Minikube (Optionally set max memory and CPUs)
```
minikube start --driver=docker --memory=4200mb --cpus=8
```

## Enable the below addons
```
minikube addons list
minikube addons enable ingress
minikube addons enable dashboard
minikube addons enable metrics-server
```

## Check Status and Dashboard
```
minikube status
minikube dashboard
```

## Build Docker image (use platform for M1 Mac)
```
cd src/
docker build --platform linux/amd64 -t clip-k8s .
```

## Test locally (use platform for M1 Mac))
```
docker run --platform linux/amd64 -it --rm clip-k8s:latest
```

## Load the image into Minikube docker
```
minikube image load clip-k8s:latest
minikube image ls
```

# Deployment 

## Deploy CLIP in Kubernetes and check the details
### NOTE : Make sure that the service-name, app name, container and target port are correct
```
cd ../deployment
kubectl apply -f .
kubectl get all
```

## Run the minikube tunnel to expose the service run cluster IP by creating a route
### NOTE : Should be run in a separate terminal and be kept on.
```
minikube tunnel
```

## Check your ingress for hostname, IP address and port
```
kubectl get ingress clip-ingress
```

## Open the FastAPI Swagger docs and tryout the API

![image](https://github.com/RSWAIN1486/k8s-local/assets/48782471/9a8f8bb5-95e7-4a34-981b-c0614683f877)

# Kubernetes Dashboard

## Workloads status

![image](https://github.com/RSWAIN1486/k8s-local/assets/48782471/21342eff-177b-459f-a31a-1e90c147b55d)

## Service and Ingress Status

![image](https://github.com/RSWAIN1486/k8s-local/assets/48782471/3ce9cdb8-4b23-4acb-ad18-ccce60da87a2)


