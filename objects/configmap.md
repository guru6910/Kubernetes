### ${\color{red} \textbf{ConfigMap}}$

````
apiVersion: v1
kind: ConfigMap
metadata:
  name: my-config
data:
  key1: value1
  key2: value2
---
apiVersion: v1
kind: Pod
metadata:
  name: my-pod
spec:
  containers:
  - name: my-container
    image: nginx
    env:
    - name: CONFIG_KEY1
      valueFrom:
        configMapKeyRef:
          name: my-config
          key: key1
    - name: CONFIG_KEY2
      valueFrom:
        configMapKeyRef:
          name: my-config
          key: key2
  restartPolicy: Never
````
