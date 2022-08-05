# Kubernetes 101

This small project was created to improve my knowledge about Kubernetes by configuring a Kubernetes setup using *minikube*.

The project is structured in the following manner:
- The *docker-compose.yml* file contains the target configuration using just Docker.
- The numbered files contain the Kubernetes configuration that mirrors the Docker target configuration and takes advantage of some of the additional features provided by Kubernetes. These files should be *applied* by numeric order.
- This *README.md* file contains some documentation of commands and resources that I found helpful while studying and developing the Kubernetes configuration.

## Starting *minikube*

To start *minikube*, run the following command on the terminal:
```
minikube start
```

## Getting running resources

To see which resources are running, run one of the following commands on the terminal:
```
kubectl get pods [-n kubernetes-101-namespace]
kubectl get replicasets [-n kubernetes-101-namespace]
kubectl get deployments [-n kubernetes-101-namespace]
kubectl get services [-n kubernetes-101-namespace]
kubectl get all [-n kubernetes-101-namespace]
kubectl get ingresses [-n kubernetes-101-namespace]
kubectl get secrets [-n kubernetes-101-namespace]
kubectl get namespaces
kubectl get endpoints [-n kubernetes-101-namespace]
```

If you are using the *default* namespace, there is no need to indicate the portion of the command that is inside brackets, but, if you are trying to list resources that are part of another namespace, like the *kubernetes-101-namespace*, you need to indicate that portion of the command without the brackets.

## Applying configuration files

To apply configuration files, run the following command on the terminal:
```
kubectl apply -f <filename> [-f <filename>]*
```

## Accessing the pods through *kubectl proxy*

To access the pods through *kubectl proxy*, run the following command on the terminal:
```
kubectl proxy
```

While this program is running, it will be possible to access the pods on the following URL:
```
http://localhost:8001/api/v1/namespaces/<namespace>/pods/<pod-name>:<pod-port>/proxy/
```
For example:

[http://localhost:8001/api/v1/namespaces/kubernetes-101-namespace/pods/readiness-pod:3000/proxy/](http://localhost:8001/api/v1/namespaces/kubernetes-101-namespace/pods/readiness-pod:3000/proxy/)
[http://localhost:8001/api/v1/namespaces/kubernetes-101-namespace/pods/site-pod:80/proxy/](http://localhost:8001/api/v1/namespaces/kubernetes-101-namespace/pods/site-pod:80/proxy/)
[http://localhost:8001/api/v1/namespaces/kubernetes-101-namespace/pods/database-admin-pod:80/proxy/](http://localhost:8001/api/v1/namespaces/kubernetes-101-namespace/pods/database-admin-pod:80/proxy/)


## Enabling support for ingresses in *minikube*

An ingress exposes HTTP and HTTPS routes from outside the cluster to services within the cluster.

To enable support for ingresses in *minikube*, run the following command on the terminal:
```
minikube addons enable ingress
```

## Getting the external IP of *minikube*

To get the external IP of *minikube*, run the following command on the terminal:
```
minikube ip
```

## Exposing a service on *minikube*

To expose a service on *minikube*, run the following command on the terminal:
```
minikube service <service> [-n <namespace>]
```

## Giving external IP address to LoadBalancer services on *minikube*

To give an external IP address to LoadBalancer services on *minikube*, run the following command on the terminal:
```
minikube tunnel
```

If you have a service of type LoadBalancer that appears as *pending* to get an external IP and you are using *minikube*, you have to run this command to obtain an external IP.

## Using the Kubernetes Dashboard UI

To use the Kubernetes Dashboard UI, refer to the following URLs:

[https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/)
[https://stackoverflow.com/questions/46664104/how-to-sign-in-kubernetes-dashboard](https://stackoverflow.com/questions/46664104/how-to-sign-in-kubernetes-dashboard)

If you are using *minikube*, you can simply run the following command on the terminal:
```
minikube dashboard
```

## Tutorials

[7 Tips and Tricks to Enjoying Your Kubernetes Journey](https://www.youtube.com/watch?v=RRCzgVI4ptY)

[Kubernetes The Easy Way!](https://www.youtube.com/watch?v=kOa_llowQ1c)

[Independent Deployment of the Frontend with Docker and Kubernetes](https://www.youtube.com/watch?v=Td7w0_nD5_4)

[Kubernetes for JavaScript Developers](https://www.youtube.com/watch?v=Zd85lFlm1pU)

[Kubernetes YAML File Explained - Deployment and Service | Kubernetes Tutorial 19](https://www.youtube.com/watch?v=qmDzcu5uY1I)

[**Kubernetes Tutorial for Beginners [FULL COURSE in 4 Hours]**](https://www.youtube.com/watch?v=X48VuDVv0do)
