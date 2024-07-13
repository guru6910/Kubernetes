#  $${\color{red} \textbf{Kubernetes}}$$

- It is developed by Google Private Cloud.
- k8s is orchastration tool.
- it manages multy containers.
- it is an open source orchastration engine for automating , deployment, scaling and management of containerized application.


${\color{red} \textbf{Kubectl : }}$

## ${\color{green} \textbf{Architecture of k8s}}$

![image](https://github.com/user-attachments/assets/d0db8be9-56a4-4089-a881-0bb53458e07b)


${\color{purple} \textbf{Master plan}}$

${\color{red} \textbf{ETCD :}}$ etcd is a crucial component that serves as the primary data store for the cluster. etcd 
is the database that Kubernetes relies on to maintain cluster state and coordinate its operations, making it fundamental to the stability, consistency, and reliability of Kubernetes clusters.

${\color{red} \textbf{Kube Schedular :}}$ The Kubernetes scheduler is a core component of Kubernetes responsible for selecting suitable nodes in the cluster to run newly created pods based on resource requirements, node capacity, and other constraints or policies. It facilitates efficient resource utilization and ensures high availability of applications by making informed decisions about pod placement within the cluster.

${\color{red} \textbf{Controller Manager :}}$ The Kubernetes Controller Manager is a core control loop that manages various controllers responsible for maintaining the desired state of the cluster. Each controller implements a different control loop to manage different aspects of the Kubernetes system, such as nodes, pods, and deployments. These controllers continuously watch the Kubernetes API server for changes and take actions to ensure that the actual state of the cluster matches the desired state defined in the Kubernetes objects.

${\color{red} \textbf{API server :}}$ the API server is the primary gateway through which users, applications, and Kubernetes components interact with the cluster, making it a fundamental component for managing and orchestrating containerized workloads in Kubernetes.

${\color{purple} \textbf{Workers}}$

${\color{red} \textbf{kublet :}}$ The Kubelet is an agent that runs on each node in the Kubernetes cluster.

${\color{red} \textbf{Kube proxy : }}$ Kube Proxy (kube-proxy) is a network proxy that runs on each node in the cluster.

${\color{red} \textbf{Container engine :}}$ The Container Engine (e.g., Docker, containerd, cri-o) is responsible for managing the container lifecycle on each node.

${\color{red} \textbf{POD :}}$ A Pod is the smallest deployable unit in Kubernetes and represents one or more containers that share the same network and storage context.


${\color{purple} \textbf{Advantages of k8s}}$
- Orchastration
- Scalability
- Availability
- Load balancing
- Rolling Updates
- Strong community support
- Self healing

${\color{purple} \textbf{k8s services of providers}}$

${\color{red} \textbf{Elastic k8s service :}}$ EKS is a managed Kubernetes service provided by Amazon Web Services (AWS).

${\color{red} \textbf{Azure K8s service :}}$ AKS is a managed Kubernetes service provided by Microsoft Azure

${\color{red} \textbf{Google kubernetes engine :}}$ GKE is a managed Kubernetes service provided by Google Cloud Platform (GCP).
