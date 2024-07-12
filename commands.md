${\color{green} \textbf{Create an AWS EC2 instance with Ubuntu 22}}$

instance size : t2.large with 2 CPUs , 32 GB Storage.

${\color{green} \textbf{Install Docker}}$

````
sudo apt update
sudo apt install apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
````
````
sudo apt update -y
apt-cache policy docker-ce -y 
sudo apt install docker.ce -y 
sudo service docker start
sudo usermod -aG docker ubuntu
newgrp docker
````


${\color{green} \textbf{Install kubectl}}$

````
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
 curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl.sha256"
echo "$(cat kubectl.sha256)  kubectl" | sha256sum --check
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
chmod +x kubectl
mkdir -p ~/.local/bin
mv ./kubectl ~/.local/bin/kubectl
````
````
kubectl version --client
````


${\color{green} \textbf{Install Minikube}}$

````
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube
minikube start
````
````
minikube stop
````


${\color{green} \textbf{create pod nginx}}$

${\color{purple} \textbf{pod.html}}$
````
apiVersion: v1
kind: Pod
metadata:
   name: pod2
spec:
 containers:
 - name: pod1
   image: httpd:latest
   ports:
   - containerPort: 80
````
${\color{green} \textbf{create pod httpd}}$

${\color{purple} \textbf{pod.html}}$
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
