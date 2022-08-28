# Kubernetes web application with mongo database

### Guides

The following application illustrate simple kubernetes cluster. It contains few modules, which is spring boot web application, mongo database server, mongo express client, k8s secret with database configuration, config map and ingress component.

The configuration and statistics can be done with using kubernetes dashboard. Project describe how to access dashboard UI.

### Installation


```
minikube start
```

Applying all k8s config files:
```
kubectl apply -f db-secret.yaml
kubectl apply -f db-config.yaml
kubectl apply -f mongo.yaml
kubectl apply -f mongo-express.yaml
kubectl apply -f webapp.yaml
kubectl apply -f ingress.yaml
```

### Accessing web application
```
minikube ip

http://<cluster_ip>:30100/
```

### Accessing mongo express client
```
minikube ip
http://<cluster_ip>:30200/
```

### Checking pod logs
```
kubectl get pod
kubectl logs <pod_name>
kubectl describe pod <pod_name>
```
### Kubernetes dashboard

#### Create account for kubernetes dashboard 
```
cd dashboard
kubectl apply -f admin-user.yaml
kubectl apply -f cluster-role.yaml
```

#### Create Bearer Token
```
kubectl -n kubernetes-dashboard create token admin-user
```

#### Accessing kubernetes dashboard

http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/



## Documentation of the libraries used
* [Kubernetes documentation](https://kubernetes.io/)
* [Kubernetes dashboard](https://github.com/kubernetes/dashboard/blob/master/docs/user/access-control/creating-sample-user.md)
* [Kubernetes example config files](https://kubernetes.io/docs/concepts/workloads/controllers/)
* [Spring boot](https://docs.spring.io/spring-boot/docs/current/reference/html/)

