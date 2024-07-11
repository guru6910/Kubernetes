#  ${\color{green} \textbf{Create an AWS EC2 instance with Ubuntu 22}}$

instance size : t2.large with 2 CPUs , 32 GB Storage.

${\color{green} \textbf{Install Docker}}$

````
sudo apt update
sudo apt install apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt install docker.io
sudo service docker start
sudo usermod -aG docker ubuntu
newgrp docker
````
