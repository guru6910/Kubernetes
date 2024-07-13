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
  - name: pod2
   image: tomcat
   ports:
   - containerPort: 8080
````

