# ${\color{red} \textbf{Volume}}$

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
When mounts the /data folder in that pod then when our container is deleted hence pod create a new container automatically that time in the new container /data have our previous data of old container bcoz we mount that folder and its volume is connected with pod not container.
