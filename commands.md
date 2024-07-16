## $${\color{violet} \textbf{Basic Commands of k8s}}$$

${\color{cyan} \textbf{pod}}$

1. Check the minikube install or not.
````
kubectl get node
````
3. Create pod.
````
kubectl apply -f <file.yaml>
````
3. Listing of pods
````
kubectl get pod
````
4. All info of particular pod.
````
kubectl describe pod <pod_name>
````
5. Show wide info of pods.
````
kubrctl get pods -o wide
````
6. Delete the pod.
````
kubectl delete pod <pod_name>
````
7. Enter the pod
````
kubectl exec <pod_name>  -it -c <container_name> -- /bin/bash
````
8. create a pod with command.
````
kubectl run nginx --image=nginx --restart=Never
````

${\color{cyan} \textbf{Replication Controller}}$


1. Create Replication controller
````
kubectl apply -f rc.yaml
````
2. List of Replication controller
````
kubectl get rc
````
3. Delete Replication Controller
````
kubectl delete rc <rc-name>
````

${\color{cyan} \textbf{Replica Set}}$

1. Create Replica set
````
kubectl appply -f rs.yaml
````
2. List of Replica Set.
````
kubectl get rs
````
3. Delete Replica set.
````
kubectl delete rs <rs-name>
````

${\color{cyan} \textbf{Deployment}}$

1. Create Deployment wit command
````
kubectl create deployment <deploy_name> --image=nginx --replicas=2
````
2. Convert yaml language which deployment created with command in particular file
````
kubectl get deployment -o yaml > <file.yaml>
````
3. list of deployment
````
kubectl get deployment
````
4. Delete the Deployment
````
kubectl delete deployment <deployment_name>
````
5. view the history of deployments, including revisions and changes
````
kubectl rollout history deployment <deployment_name>
````
6. Update the image Version.
````
kubectl set image deployment/<deployment_name> nginx=<new_version>
````
