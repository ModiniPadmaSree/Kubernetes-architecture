Master and Worker Nodes in Kubernetes \
 \
A Kubernetes cluster consists of two main types of nodes:
1. Master Node (Control Plane)

2. Worker Nodes
1. Master Node (Control Plane) \
The Master Node is responsible for managing the entire cluster.

It does not run application containers. Instead, it controls scheduling, state management, and cluster operations.
 \
Master Node Components:
- API Server \
Entry point for all cluster communication. \
Processes REST requests from kubectl and other tools \
Validates and stores data in etcd.

- Scheduler \
Assigns newly created Pods to appropriate worker nodes. \
Considers: \
CPU and memory availability \
Node labels \
Taints and tolerations \
Affinity rules
- Controller Manager \
Runs background controllers such as: \
Node Controller \
ReplicaSet Controller \
Deployment Controller \
Job Controller \
Ensures desired state equals actual state.
- etcd \
Distributed key-value store. \
Stores all cluster configuration and state data.
2. Worker Nodes \
Worker nodes are responsible for running application workloads. \
Each worker node contains:
- Kubelet \
Agent running on each worker.\
Communicates with API server. \
Ensures containers are running as expected.
- Kube Proxy
Manages networking rules. \
Enables Service-based communication. \
Provides internal load balancing. \
Container Runtime \
Runs containers. \
Examples: containerd, CRI-O \
\
How Master and Worker Nodes Work Together \
User submits request using kubectl. \
API Server receives request. \
Scheduler assigns Pod to a worker node. \
Kubelet starts container on that node. \
Controller Manager ensures replica count is maintained. \
In managed cloud services (EKS, AKS, GKE), the Master Node is maintained by the cloud provider.
