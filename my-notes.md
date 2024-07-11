#  $${\color{red} \textbf{Kubernetes}}$$

- It is developed by Google Private Cloud.
- k8s is orchastration tool.
- it manages multy containers.
- it is an open source orchastration engine for automating , deployment, scaling and management of containerized application.

#  ${\color{green} \textbf{Architecture of k8s}}$


${\color{purple} \textbf{Master plan}}$

${\color{red} \textbf{ETCD :}}$ etcd is a crucial component that serves as the primary data store for the cluster. etcd 
is the database that Kubernetes relies on to maintain cluster state and coordinate its operations, making it fundamental to the stability, consistency, and reliability of Kubernetes clusters.

${\color{red} \textbf{Kube Schedular :}}$ The Kubernetes scheduler is a core component of Kubernetes responsible for selecting suitable nodes in the cluster to run newly created pods based on resource requirements, node capacity, and other constraints or policies. It facilitates efficient resource utilization and ensures high availability of applications by making informed decisions about pod placement within the cluster.

${\color{red} \textbf{Controller Manager :}}$ The Kubernetes Controller Manager is a core control loop that manages various controllers responsible for maintaining the desired state of the cluster. Each controller implements a different control loop to manage different aspects of the Kubernetes system, such as nodes, pods, and deployments. These controllers continuously watch the Kubernetes API server for changes and take actions to ensure that the actual state of the cluster matches the desired state defined in the Kubernetes objects.

${\color{red} \textbf{API server :}}$ the API server is the primary gateway through which users, applications, and Kubernetes components interact with the cluster, making it a fundamental component for managing and orchestrating containerized workloads in Kubernetes.

