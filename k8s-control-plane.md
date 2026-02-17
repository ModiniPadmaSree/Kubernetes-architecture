Kubernetes Control Plane Components \

The Control Plane is responsible for managing the Kubernetes cluster. \

It makes global decisions about: Scheduling, Scaling, Maintaining cluster state \
1. API Server: The API Server is the central management component.

Responsibilities:

- Accepts REST requests

- Authenticates and authorizes users

- Validates requests

- Updates cluster state in etcd

- Acts as communication hub for all components

- All cluster operations pass through the API Server.
2. etcd: etcd is a distributed key-value database.

Responsibilities:

- Stores cluster configuration

- Stores Secrets

- Stores metadata of Pods, Services, Deployments

- Maintains desired and current state

- It is critical for cluster consistency and reliability.
3. Controller Manager: The Controller Manager runs multiple controllers in the background.

Each controller watches cluster state and ensures: \
Actual State = Desired State \

Examples:

Replica Controller

Deployment Controller

Node Controller
4. Scheduler: The Scheduler assigns Pods to nodes.

It considers: \
Resource availability,

Node conditions,

Affinity/anti-affinity rules,

Taints and tolerations,

Once a node is selected, the Pod is bound to that node.
 \
Control Plane Workflow \

1. User creates a Deployment.

2. API Server validates request.

3. Desired state is stored in etcd.

4. Scheduler assigns Pods.

5. Controller Manager ensures correct number of replicas.

6. Kubelet executes on worker nodes.
