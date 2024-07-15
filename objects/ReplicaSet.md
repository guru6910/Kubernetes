${\color{purple} \textbf{pod.yaml}}$

````
apiVersion: apps/v1
kind: ReplicaSet
metadata:
 name: nginx
 labels:
   app: nginx-app
spec:
 replicas: 2
 selector:
    matchLabels:
      app: nginx-app
 template:  
  metadata:
   labels: 
     app: nginx-app
  spec:
   containers:
   - name: cont1 
     image: nginx:latest
     ports:
     - containerPort: 80
````




````
apiVersion: apps/v1
kind: ReplicaSet
metadata:
 name: nginx
 labels:
   app: nginx-app
spec:
 replicas: 2
 selector:
    matchExpressions:
      - key: app
        operator: In
        values:
        - nginx-app 
 template:  
  metadata:
   labels: 
     app: nginx-app
  spec:
   containers:
   - name: cont1 
     image: nginx:latest
     ports:
     - containerPort: 80
````
