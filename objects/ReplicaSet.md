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

## ${\color{green} \textbf{In}}$
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

## ${\color{green} \textbf{NotIn}}$

````
apiVersion: apps/v1
kind: ReplicaSet
metadata:
 name: nginx-app
 labels:
    app: nginx-app
spec:
  replicas: 3
  selector:
     matchExpressions:
       - key : app
         operator: NotIn
         values:
         - nginx-app

  template:
     metadata:
       name: nginx-temp
       labels:
          app: nginx-app
     spec:
       containers:
        - name: nginx-cont
          image: nginx:latest
          ports:
          - containerPort: 80

  template:
     metadata:
       name: httpd-temp
       labels:
          app: httpd
     spec:
       containers:
        - name: httpd
          image: httpd:latest
          ports:
          - containerPort: 81
````
## ${\color{green} \textbf{Exists}}$
````
# ReplicaSet With Exits set based selector
apiVersion: apps/v1
kind: ReplicaSet
metadata:
 name: nginx-app
 labels:
    app: nginx-app
spec:
  replicas: 3
  selector:
     matchExpressions:
       - key : app
         operator: Exists

  template:
     metadata:
       name: nginx-temp
       labels:
          app: nginx-app
     spec:
       containers:
        - name: nginx-cont
          image: nginx:latest
          ports:
          - containerPort: 80

  template:
     metadata:
       name: httpd-temp
       labels:
          app: httpd
     spec:
       containers:
        - name: httpd
          image: httpd:latest
          ports:
          - containerPort: 81
````

## Selectors

Equality Based Selector

- it is old version of selectors
- we use Equality based in Replication controoler for manage with pod
- it define with key:value
 
Set Based Selector

- it is updated version of selector
- we use Set based in Replica set and Replication controller also.
- it define with
- In = key: value
- NotIN = key: value : avoid it and run
- Exists = env{ } : run all which hav in that env 
