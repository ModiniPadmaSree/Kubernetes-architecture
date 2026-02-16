Kubernetes is a container orchestration platform used to automate the deployment, scaling, and management of containerized applications. The following are the main workload and configuration components used in Kubernetes. \
1. Pods: A Pod is the smallest and most basic deployable object in Kubernetes. It represents a single instance of a running application. \
Key Characteristics:
- Contains one or more containers.
- Containers inside a pod share:
- The same IP address
- Network namespace
- Storage volumes
- Pods are ephemeral (they can be created and destroyed dynamically).
- Usually managed by higher-level objects like Deployments.
2. Services: A Service is used to expose a group of Pods as a network service.
Since Pods are dynamic and their IP addresses change frequently, Services provide a stable IP and DNS name for communication. \
Types of Services:
- ClusterIP: Default type, accessible only within the cluster
- NodePort: Exposes the service on a static port on each node
- LoadBalancer: Creates a cloud load balancer, used in cloud environments (EKS, AKS, GKE)
- ExternalName: Maps service to external DNS name
3. Deployments: A Deployment manages the lifecycle of Pods.

It ensures the desired number of Pods are always running and allows controlled updates. \
Key Features:

- Rolling updates

- Rollbacks

- Scaling applications

- Self-healing (restarts failed pods) \
Why Deployments Are Used: Instead of manually creating Pods, Deployments automate:

- Pod creation

- Replica management

- Update strategies

- Deployments internally manage ReplicaSets.
4. ReplicaSets: A ReplicaSet ensures that a specified number of identical Pods are running at all times. \
If a Pod crashes: ReplicaSet automatically creates a new one. \
Although ReplicaSets can be used directly, they are usually managed by Deployments.
5. ConfigMaps: A ConfigMap stores non-sensitive configuration data in key-value format. \
Examples: Environment variables, Database hostnames, Application configuration values \
Purpose: Separates configuration from application code, making applications more portable and easier to manage.
6. Secrets: A Secret stores sensitive information such as:

- Passwords

- API keys

- Tokens

- Certificates \
Secrets are stored securely (base64 encoded) and can be injected into Pods as: \
- Environment variables
- Mounted files
Importance: Improves security by preventing hardcoding credentials inside container images.
