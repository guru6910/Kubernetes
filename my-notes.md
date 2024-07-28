#  $${\color{red} \textbf{Kubernetes}}$$

- It is developed by Google Private Cloud.
- k8s is orchastration tool.
- it manages multy containers.
- it is an open source orchastration engine for automating , deployment, scaling and management of containerized application.
- K8s has two versions, the original Kubernetes and a mini version which is known as minikube.

${\color{red} \textbf{Kubectl : }}$ give access for kubernetes commands.

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


${\color{green} \textbf{Labels :}}$  Key-value pairs assigned to Kubernetes objects for organization and selection.

${\color{green} \textbf{Replicas :}}$  The desired number of identical pod instances to run.


## Selectors
Criteria used to identify and manage groups of labeled objects.

${\color{red} \textbf{Equality Based}}$

- it is old version of selectors
- we use Equality based in Replication controoler for manage with pod
- it define with key:value
  
${\color{red} \textbf{Set Based}}$
 
- it is updated version of selector
- we use Set based in Replica set and Replication controller also.
- it define with
- In = key: value
- NotIN = key: value : avoid it and run
- Exists = env{ } : run all which hav in that env 


###  ${\color{red} \textbf{Replication Controller : }}$  

Replication control in Kubernetes (K8s) ensures that a specified number of pod replicas are running at any given time. It automatically replaces any pods that fail, maintaining the desired state specified by the user.

###  ${\color{red} \textbf{Replica Set : }}$  

A ReplicaSet in Kubernetes ensures that a specified number of pod replicas are running at any given time. If a pod fails or is deleted, the ReplicaSet automatically creates a new one to maintain the desired number of replicas.

![image](https://github.com/user-attachments/assets/656a1be5-d1b2-4674-9b64-d6577cbaf64d)


###  ${\color{red} \textbf{Deployment : }}$

In Kubernetes (k8s), a deployment is a way to manage and update applications running in your cluster. It defines the desired state for your app, such as how many copies of the app should be running, and Kubernetes ensures that the current state matches the desired state. If something goes wrong, Kubernetes can automatically restart or replace instances to keep your app running smoothly.


###  ${\color{green} \textbf{Strategy}}$

${\color{purple} \textbf{1. Recreate Strategy}}$

**What it does:** Stops all existing pods before starting new ones.

**How it works:** Kubernetes first shuts down all the existing pods running the old version of the application.
Once the old pods are terminated, it starts creating new pods with the updated version.

**When to use:** When downtime is acceptable, and you need to ensure that no old version of the application is running during the update.

**Example:** Used for non-critical applications or during maintenance windows.

${\color{purple} \textbf{2. Rolling Update Strategy}}$

**What it does:** Gradually replaces old pods with new ones without downtime.

**How it works:**
Kubernetes updates a few pods at a time (based on the update settings) with the new version.
Ensures that there are always some pods available to serve requests during the update process.
When to use: When you need to update the application without any downtime and ensure continuous availability.

**Example:** Suitable for web services or user-facing applications where availability is critical.


${\color{purple} \textbf{3. Blue-Green Deployment}}$

**What it does:** Maintains two environments (blue and green) and switches traffic between them.

**How it works:** The new version of the application is deployed to the green environment while the blue environment runs the old version.
Once the green environment is ready and tested, traffic is switched from blue to green.
The blue environment can be kept as a fallback in case of issues with the green environment.

**When to use:** When you need a safe and easy way to switch back to the old version in case of problems.

**Example:** Useful in environments where high availability and quick rollback are required.

${\color{purple} \textbf{4. Canary Deployment}}$

**What it does:** Gradually routes a small percentage of traffic to the new version before fully switching over.

**How it works:** Deploys the new version to a small subset of users (canary pods).
Monitors the performance and health of the canary pods.
If successful, gradually increases the traffic to the new version until it replaces the old one completely.

**When to use:** When you want to test the new version in a production environment with minimal risk.

**Example:** Ideal for incremental updates and testing new features with a small user base.


${\color{purple} \textbf{5. A/B Testing}}$

**What it does:** Runs multiple versions of an application simultaneously and directs traffic to them based on specific criteria.

**How it works:** Different versions (A and B) are deployed, and traffic is split between them based on user characteristics or other metrics.
Used to compare performance, user engagement, or other metrics between the versions.

**When to use:** When you need to evaluate different versions of an application against each other based on real user interactions.

**Example:** Often used for user experience testing, feature flagging, and market experiments


### ${\color{red} \textbf{Deployments Type}}$

${\color{green} \textbf{Stateless Applications}}$


**Description:** Stateless applications do not store any data or state locally on the pod that cannot be lost. They handle requests independently, and any necessary data is typically stored in an external service like a database.

**Use Cases:**
- Web servers
- API servers
- Frontend applications

**Deployment Controller:** Deployments or ReplicaSets are typically used for stateless applications.


${\color{green} \textbf{Stateful Applications}}$

**Description:** Stateful applications require persistent storage and maintain state information across pod restarts and rescheduling. Each instance of a stateful application (pod) usually has a unique identifier and stable network identity.

**Use Cases:**

- Databases (e.g., MySQL, Cassandra)
- Distributed file systems
- Stateful services requiring persistent data

**Deployment Controller:** StatefulSets are used for deploying stateful applications.


## ${\color{brown} \textbf{Key Differences}}$

### 1. State Management:

**Stateless:** No persistent state, each request is independent.

**Stateful:** Maintains state across requests and pod restarts.

### 2. Pod Identity:

**Stateless:** Pods are interchangeable, no unique identifiers.

**Stateful:** Each pod has a unique identity and stable network name.

### 3. Storage:

**Stateless:** Does not require persistent storage.

**Stateful:** Requires persistent storage, typically using PersistentVolumes.

### 4. Deployment Strategy:

**Stateless:** Use Deployments or ReplicaSets.

**Stateful:** Use StatefulSets.

### 5. Scaling:

**Stateless:** Easier to scale horizontally since there is no state dependency.

**Stateful:** More complex to scale due to state and data consistency requirements.


![image](https://github.com/user-attachments/assets/9400765c-5db3-4a4b-8e58-fd42f22517d9)


## ${\color{red} \textbf{Namespace}}$

- A namespace is a way to divide cluster resources between multiple users.
- It allows you to create multiple virtual clusters within the same physical cluster.
- Namespaces provide a scope for names and help in organizing and managing resources.
-  Namespaces provide a level of isolation for objects like pods, services, and deployments.
-  When you create a resource without specifying a namespace, it gets created in the default namespace.


### Default Namespace:

**1. default:** This is the default namespace for objects without an explicit namespace. If you don’t specify a namespace when creating a resource, it goes into the default namespace.

**2. kube-system:** Used for Kubernetes system components.

**3. kube-public:** Used for resources that should be publicly accessible within the cluster.

**4. kube-node-lease:** Holds lease objects associated with each node to determine node health.

**5. local-path-storage:** Local path storage can be used as the default storage option.


## ${\color{red} \textbf{Service}}$

A Service is like a middleman that helps different parts of your application talk to each other. It gives a stable network address so other parts can find and use it, even if the actual parts (called Pods) that do the work change over time. 

It's like having a reliable phone number that always reaches a customer support team, even if the people answering the phones change.

### Service Types:

- ${\color{pink} \textbf{ClusterIP:}}$ Exposes the service on a cluster-internal IP. This type makes the service only reachable from within the cluster.

![image](https://github.com/user-attachments/assets/05b4c84e-86ca-4961-8dd7-9f1bad4a3245)


- ${\color{pink} \textbf{NodePort:}}$ Exposes the service on each Node’s IP at a static port. A ClusterIP service, to which the NodePort service routes, is automatically created.

![image](https://github.com/user-attachments/assets/adaee991-dcf1-4988-b281-9e2245976285)

  
- ${\color{pink} \textbf{LoadBalancer:}}$ Exposes the service externally using a cloud provider’s load balancer. NodePort and ClusterIP services, to which the external load balancer routes, are automatically created.

![image](https://github.com/user-attachments/assets/ab121db2-6e2e-440a-bc79-2ec04c483219)


- ${\color{pink} \textbf{ExternalName:}}$  Maps the service to the contents of the externalName field (e.g., example.com), returning a CNAME record with the name. No proxying of any kind is set up.

## ${\color{red} \textbf{DaemonSet}}$

A DaemonSet in Kubernetes is a way to automatically run a particular pod on all or specific nodes in a cluster. It's useful for tasks like monitoring or logging where you want the same service running across the entire cluster. If you create a DaemonSet, Kubernetes ensures that the pod is scheduled on every node, ensuring the task is consistently covered.

![image](https://github.com/user-attachments/assets/31434f9e-1e11-4ac0-adb0-c428ee427785)


## ${\color{red} \textbf{Volume}}$

volume is a directory accessible to containers in a pod. Volumes solve issues related to data persistence and sharing among containers.

Type of Volume.

${\color{green} \textbf{EmptyDir :}}$ 
- An empty directory created for a pod, accessible to all containers within that pod. It exists as long as the pod is running.

![image](https://github.com/user-attachments/assets/80820051-4840-4302-bcaf-92ce2a6cea97)


${\color{green} \textbf{hostPath :}}$ 
- Mounts a file or directory from the host node’s filesystem into your pod.

![image](https://github.com/user-attachments/assets/50fd534a-ec7c-44d5-9618-b159f7112995)


${\color{green} \textbf{PersistentVolumeClaim :}}$ 

![image](https://github.com/user-attachments/assets/47012cce-bc66-4059-820c-fc7283cffaca)


- Claims storage resources defined by a PersistentVolume (PV). It's a way to request dynamically provisioned storage.
- in thaat case volume is created with ebs in storage the it distributed in parts and it usage to pod using pvc.
- when our deleted pod create in another node hence our previous data accisable for newly pod which create in different node.

${\color{green} \textbf{Access Modes:}}$

**1. ReadWriteOnce (RWO):**
- The volume can be mounted as read-write by a single node.

**2. ReadOnlyMany (ROX):**
- The volume can be mounted as read-only by many nodes.

**3. ReadWriteMany (RWX):**
- The volume can be mounted as read-write by many nodes.

${\color{green} \textbf{Persistent Volume Reclaim Policy}}$
- This policy determines what happens to a PersistentVolume (PV) when its associated PersistentVolumeClaim (PVC) is deleted.

**1. Retain:**
- The PV is not deleted. it not reuse with another pv.

**2. Delete:**
- The PV and its data are deleted along with the PVC. This is useful for dynamic provisioning.

**3. Recycle:**
- The PV’s data is scrubbed (basic data wipe) and the PV is made available for a new claim. 


## ${\color{red} \textbf{StatefulSet}}$
- A StatefulSet is a Kubernetes controller that manages the deployment and scaling of a set of Pods and provides guarantees about the ordering and uniqueness of these Pods.
- It is specifically designed to manage stateful applications, which require persistent storage and stable network identities.
- StatefulSets provide stable, persistent storage for each Pod. This is typically achieved through PersistentVolumeClaims (PVCs) that are created for each Pod. The storage remains even if the Pod is deleted and recreated.
- Pods in a StatefulSet are deployed in a specific order, one at a time, and are terminated in reverse order. This ensures that the system maintains a predictable state during scaling operations.
- 

![image](https://github.com/user-attachments/assets/d62aff60-458e-4805-a03a-0a79a1de00ed)
