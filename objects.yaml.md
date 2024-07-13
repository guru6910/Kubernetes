${\color{purple} \textbf{pod.yaml}}$
````
apiVersion: v1
kind: Pod
metadata:
   name: pod2
spec:
 containers:
 - name: pod1
   image: nginx:latest
   ports:
   - containerPort: 80
````

${\color{purple} \textbf{replication-controller.yaml}}$
````
apiVersion: v1
kind: ReplicationController
metadata:
 name: rc-demo
 labels:
  env: dev

spec:
 replicas: 3
 selector:
    env: dev
 template:
   metadata:
    labels:
      env: dev
   spec:
    containers:
    - name: demo
      image: nginx
      ports:
      - containerPort: 80
````
