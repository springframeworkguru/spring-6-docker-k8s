# Images
* `spring-6-gateway:0.0.1-SNAPSHOT`
* `spring-6-auth-server:0.0.1-SNAPSHOT`
* `spring-6-rest-mvc:0.0.1-SNAPSHOT`
* `spring-6-reactive:0.0.1-SNAPSHOT`
* `reactive-mongo:0.0.1-SNAPSHOT`

Display all K8s resources in the default namespace
```bash
kubectl get all
```

Display all K8s resources in the default namespace with more details
```bash 
kubectl get all -o wide
```

Create Deployment for Mongo
```bash
kubectl create deployment mongo --image=mongo --dry-run=client -o yaml > mongo-deployment.yaml
```

Apply Deployment
```bash
kubectl apply -f mongo-deployment.yaml
```

Create Service for Mongo
```bash
kubectl create service clusterip mongo --tcp=27017:27017 --dry-run=client -o yaml > mongo-service.yaml
```

Apply Service for Mongo
```bash
kubectl apply -f mongo-service.yaml
```

Delete Service for Mongo
```bash
kubectl delete service mongo
```

Delete Deployment for Mongo
```bash
kubectl delete deployment mongo
```

View logs for Mongo
```bash 
kubectl logs mongo-<pod-id>
```


Create Deployment for Auth-server
```bash
kubectl create deployment auth-server --image=spring-6-auth-server:0.0.1-SNAPSHOT --dry-run=client -o yaml > auth-server-deployment.yaml
```

Apply Deployment for Auth-server
```bash
kubectl apply -f auth-server-deployment.yaml
```

Create Service for Auth-server
```bash
kubectl create service clusterip auth-server --tcp=9000:9000 --dry-run=client -o yaml > auth-server-service.yaml
```

Apply Service for Auth-server
```bash
kubectl apply -f auth-server-service.yaml
```

Port forward to Gateway
```bash
kubectl port-forward service/gateway 8080:8080
```