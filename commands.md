## ${\color{green} \textbf{Basic Commands of k8s}}$

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
7. Create Replication controller
````
kubectl apply -f rc.yaml
````
8. List of Replication controller
````
kubectl get rc
````
9. Delete Replication Controller
````
kubectl delete rc <rc-name>
````
