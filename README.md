# Kubernetes Hello World Application

This README outlines the steps to build, run, and deploy a simple "Hello World" web application using Docker and Kubernetes.

## Prerequisites

- Ubuntu VM
- Docker Desktop 
- kubectl 

## Getting Started

### Install kubectl

Follow instructions here: https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/

### Install minikube

Follow instructions here: https://minikube.sigs.k8s.io/docs/start/


## New sessions

Run the following commands


```bash
minikube start
docker login
```

Then follow this tutorial: https://medium.com/@aris.david/running-kafka-producer-and-consumer-on-a-local-kubernetes-cluster-fe85df25ca92

### Build the Docker Image

Navigate to the project directory and build your Docker image:

```bash
cd path/to/your/project
docker build -t hello-kubernetes .
```

## Run Your Docker Container Locally

Run your Docker image as a container, mapping the container's port to a port on your host:

```bash
docker run -p 4000:5000 hello-kubernetes
```

Access your application by navigating to http://localhost:4000 in your web browser.


## Deploying to Kubernetes

### Open a New Terminal Window
When deploying to Kubernetes, it's best to use a new terminal window to keep your Docker container running.

### Apply Kubernetes Deployment
Deploy your application to Kubernetes using the deployment configuration:

```bash
kubectl apply -f deployment.yaml
```

### Apply Kubernetes Service
Expose your application outside of Kubernetes using the service configuration:

```bash
kubectl apply -f service.yaml
```


### Accessing Your Application
Since LoadBalancer might not work as expected on Docker Desktop, use port forwarding:
```bash
kubectl port-forward service/hello-kubernetes-service 8000:80
```

Access your application by navigating to http://localhost:8000 in your web browser.


## Deleting the Deployment
When you are finished, delete the deployment:
```bash
kubectl delete deployment hello-kubernetes
```