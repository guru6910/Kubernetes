### 1. Add Bitnami Helm repository
```
helm repo add bitnami https://charts.bitnami.com/bitnami
```
```
helm repo update
```
### 2. Install NGINX with LoadBalancer type service
```
helm install my-nginx bitnami/nginx --set service.type=LoadBalancer
```
### 3. Watch for the external IP (wait until it appears)
```
kubectl get svc my-nginx -w
```
### 4. Host that LoadBalancer link on browser. 
