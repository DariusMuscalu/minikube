# Minikube local deployment example

This project demonstrates an ideal deployment setup for a minimal Kubernetes application on your local machine. It includes the following components:

- Kubernetes (using Minikube)
- Basic Hello World node web server Docker image
- Kubernetes Pod that uses the Hello World Docker image
- Kubernetes Service for the Pod
- Exposing the service using Port Forwarding

## Table of Contents

- [Prerequisites](#prerequisites)
- [Running the Application](#running-the-application)

## Prerequisites

List any prerequisites or dependencies that need to be installed on the user's machine before running the project.

- [Docker](https://www.docker.com/get-started)
- [Minikube](https://minikube.sigs.k8s.io/docs/start/)
- [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)

## Running the application

1. Clone the repository:
```bash
git clone https://github.com/DariusMuscalu/minikube
cd minikube
```

2. Build the Docker image for the Hello World web server:
```bash
docker build -t hello-world-app .
```

3. Load the Docker image into Minikube:
```bash
minikube image load hello-world-app
```

4. Start Minikube:
```bash
minikube start
```
- To check that minikube started successfully use:
```bash
minikube status
```

5. Apply the Kubernetes deployment and service configurations:
```bash
kubectl apply -f ./k8/deployment/deployment.yaml
kubectl apply -f ./k8/service.yaml
```
- This will create the deployment and service in your Minikube cluster.

6. Use port forwarding to access the application:
```bash
kubectl port-forward service/minikube-app-service 3000:80
```

This will expose the application on http://localhost:3000.