${\color{red} \textbf{Namespace}}$


````
apiVersion: v1
kind: Namespace
metadata:
  name: my-namespace

````

${\color{red} \textbf{Namespace use in pod}}$
````
apiVersion: v1
kind: Pod
metadata:
  name: my-pod
  namespace: my-namespace
spec:
  containers:
  - name: my-container
    image: nginx
    ports:
    - containerPort: 80
````
