${\color{red} \textbf{Deployment}}$

````
apiVersion: apps/v1
kind: Deployment
metadata:
  name: deployment-1
spec:
  replicas: 3
  selector:
    matchLabels:
      app: my-app
  template: 
    metadata:
      labels:
        app: my-app
    spec: 
      containers: 
      - name: cont1
        image: httpd:latest
        ports:
        - containerPort: 80
````


````
apiVersion: apps/v1
kind:  Deployment
metadata: 
  name: deploy
  labels:
    app: depapp
spec:
    strategy:
      type: RollingUpdate
      rollingUpdate:
            maxSurge: 1     # Maximum number of pods that can be created over the desired replicas
            maxUnavailable: 1  # Maximum number of pods that can be unavailable during the update
    selector: 
      #matchExpressions:      
         #  -  { key: app, operator: In , values: [rsapp,  new-app]}
         #   -  { key: app, operator: Exists}
      matchLabels: 
          app: depapp
    replicas: 10
    template:
      metadata:
        labels:
          name: nginxapp
          app: depapp
      spec:
        containers:
          - name: nginxapp
            image: httpd:latest 
            ports:
                - containerPort: 80
                  protocol: TCP
````
