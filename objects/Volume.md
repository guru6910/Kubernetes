${\color{red} \textbf{Volume}}$

${\color{green} \textbf{EmptyDir}}$
````
apiVersion: v1 
kind: Pod
metadata: 
  name: pod-1
spec: 
  containers:
  - image: nginx
    name: cont-1
    volumeMounts: 
      - mountPath: /data
        name: vol-1
  volumes:
  - name: vol-1
    emptyDir: {}
````
