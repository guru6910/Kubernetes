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


${\color{green} \textbf{HostPath}}$
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
      - mountPath: /data  #it path in the pod.
        name: vol-1
  volumes:
  - name: vol-1
    hostPath:
      path: /tmp/data  #it is a local path in node.
````

In that case our volume is stored on worker node thats why when our node is terminated and newly created that time volume is attached with newly created pod.

we mounted the /data folder when pod deleted and its newly created that time newly pod have old pod data which was have in /data folder not have any other directory old data which we created in that.


