# Task 5 — Kubernetes with Minikube

## - Objective

Set up a local Kubernetes cluster using Minikube, deploy an Nginx application, expose it as a service, scale the deployment, view logs, perform a rolling update, and clean up resources.

---

## - Prerequisites

* ` Docker` installed & running
* `kubectl` CLI installed
* `minikube` installed

---

## - Steps Performed

### 1. Start Minikube

```bash
minikube start --driver=docker --cpus=2 --memory=4096
minikube status
kubectl cluster-info

```
### 2.Create Deployment

```bash
kubectl apply -f deployment.yaml
kubectl get deployments
kubectl get pods -l app=nginx

### 4. Create Service

```bash
kubectl apply -f service.yaml
kubectl get svc nginx-service
kubectl describe svc nginx-service

### 5. Access the Application

```bash
minikube service nginx-service --url
http://192.168.49.2:30080

### 6. Scaling

```bash
kubectl scale deployment/nginx-deployment --replicas=5
kubectl get pods -l app=nginx

### 7. Logs & Describe

```bash
kubectl describe pod nginx-deployment-6f8d5bcb9f-4gr6w 

### 8. Rolling Update

```bash
kubectl set image deployment/nginx-deployment nginx=nginx:1.25
kubectl rollout status deployment/nginx-deployment

### 9. Cleanup

```bash
kubectl delete -f service.yaml
kubectl delete -f deployment.yaml
minikube stop
minikube delete

### 10. Screenshots are available

## THANK YOU
