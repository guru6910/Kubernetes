${\color{purple} \textbf{pod.yaml}}$


${\color{pink} \textbf{Equality based Selector}}$
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


${\color{pink} \textbf{Set based Selector}}$

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



## ${\color{red} \textbf{Selectrs}}$


${\color{green} \textbf{Equality Based Selector :}}$
- it is old version of selectors
- we use Equality based in Replication controoler for manage with pod
- it define with key:value

${\color{green} \textbf{Set Based Selector :}}$
- it is updated version of selector
- we use Set based in Replica set and Replication controller also.
- it define with
- In = key: value
- NotIN = key: value < avoid it and run>
- Exists = env{ } <run all which hav in that env>
