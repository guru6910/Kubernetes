${\color{red} \textbf{Replica Set}}$


${\color{purple} \textbf{Equality :}}$
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


${\color{purple} \textbf{Set :}}$

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


## Selectors


### Equality Based Selector

- it is old version of selectors
- we use Equality based in Replication controoler for manage with pod
- it define with key:value
 
### Set Based Selector

- it is updated version of selector
- we use Set based in Replica set and Replication controller also.
- it define with
- In = key: value
- NotIN = key: value : avoid it and run
- Exists = env{ } : run all which hav in that env 
