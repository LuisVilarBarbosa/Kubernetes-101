# Kubernetes 101

This small project was created to improve my knowledge about Kubernetes by configuring a Kubernetes setup using minikube.

## Accessing the pods through *kubectl proxy*

To access the pods through *kubectl proxy*, run the following command on the terminal:
```
kubectl proxy
```

While this program is running, it will be possible to access the pods on the following URL:
```
http://localhost:8001/api/v1/namespaces/default/pods/<pod-name>:<pod-port>/proxy/
```
For example:
```
http://localhost:8001/api/v1/namespaces/default/pods/readiness-pod:3000/proxy/
http://localhost:8001/api/v1/namespaces/default/pods/site-pod:80/proxy/
http://localhost:8001/api/v1/namespaces/default/pods/database-admin-pod:80/proxy/
```

## Enabling support for ingresses in minikube

To enable support for ingresses in minikube, run the following command on the terminal:
```
minikube addons enable ingress
```
