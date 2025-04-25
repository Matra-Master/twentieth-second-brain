---
created: 20250210-1453
tags:
  - Resources/minikube
  - Resources/kubernetes
---
Kubernetes 101 also uses minikube so here's a mixin of both.

# Minikube

## Installed with pacman
``` bash
sudo pacman -S minikube kubectl
```
### Create a minikube cluster
``` bash
minikube start
```

### Open minikube dashboard
``` bash
minikube dashboard
```

### Create a Deployment

A Deployment is the way to manage Pods
``` bash
# Run a test container image that includes a webserver
kubectl create deployment hello-node --image=registry.k8s.io/e2e-test-images/agnhost:2.39 -- /agnhost netexec --http-port=8080
```
View the deployment
``` bash
kubectl get deployments
```

View the pod
```bash
kubectl get pods
```

Check up cluster events. Those show the list of steps taken by the deployment.
```bash
kubectl get events
```

View the kubectl configuration
```bash
kubectl config view
```

View application lgos
```bash
kubectl logs hello-node-5f76cf6ccf-br9b5
````

###  Create a Service

By default a pod is not accessible from outside. A cluster is a closed encapsulated network, like docker.
The Pod created in the last steps must be exposed as a [k8s service](https://kubernetes.io/docs/concepts/services-networking/service/).

```bash
# Create the service
kubectl expose deployment hello-node --type=LoadBalancer --port=8080

# View the service
kubectl get services

# Open the service on the browser
minikube service hello-node
```


## Definitions

### Pods

A Kubernetes [_Pod_](https://kubernetes.io/docs/concepts/workloads/pods/) is a group of one or more Containers, tied together for the purposes of administration and networking.
There are **two types:** Pods that run a single container, Pods that run multiple containers tighly coupled together.

> [!NOTE]
>  Restarting a container in a Pod should not be confused with restarting a Pod. A Pod is not a process, but an environment for running container(s). A Pod persists until it is deleted.

### Deployment

It's a declarative update of a set of Pods or ReplicaSets. You declare the *desired state* in a deployment file and a Controller takes care of making that state happen.


## Cleanup

```bash
kubectl delete service hello-node
kubectl delete deployment hello-node
# Optional
minikube delete
```

---
# Sources

https://kubernetes.io/docs/tutorials/hello-minikube/
https://minikube.sigs.k8s.io/docs/tutorials/kubernetes_101
