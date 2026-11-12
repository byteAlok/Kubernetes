# ☸️ Kubernetes – Learning & Practical Series

A hands-on journey to learning Kubernetes, container orchestration, cluster management, and cloud-native application deployment through practical examples, YAML manifests, commands, and real-world implementations.

## 📌 About This Repository

This repository documents my complete Kubernetes learning journey, starting from the fundamentals of container orchestration to advanced cluster management and production-level deployment practices.

Each topic is organized day-wise with detailed explanations, executable commands, YAML configurations, practical examples, and hands-on exercises.

### 🎯 Learning Objectives

- ☸️ Understand Kubernetes fundamentals and architecture.
- 🏗️ Learn Control Plane and Worker Node components.
- 📦 Work with Pods, ReplicaSets, and Deployments.
- 🌐 Understand Services and Kubernetes Networking.
- ⚙️ Create and manage YAML Manifests.
- 📈 Learn Scaling, Load Balancing, and Self-Healing.
- 💾 Understand Persistent Volumes and Storage.
- 🔐 Learn ConfigMaps, Secrets, RBAC, and Security.
- 📊 Monitor and troubleshoot Kubernetes clusters.
- 🚀 Deploy and manage real-world applications.
- ☁️ Integrate Kubernetes with Cloud and CI/CD platforms.

---

## 📖 Introduction to Kubernetes

**Kubernetes (K8s)** is an open-source container orchestration platform used to automate the deployment, scaling, and management of containerized applications.

When applications run inside containers, managing multiple containers across different servers becomes challenging.

Kubernetes solves this problem by providing a platform to manage containerized applications across a cluster of machines.

It helps maintain application availability, automatically replace failed Pods, scale workloads, and manage application networking.

### 🤔 Why Kubernetes?

Consider an application running inside multiple Docker containers.

As application traffic increases, we may need to:
- Run additional application instances.
- Distribute traffic between containers.
- Restart failed containers.
- Manage containers across multiple servers.
- Maintain application availability during updates.

Managing all these operations manually becomes difficult.

**Kubernetes automates these operations through Container Orchestration.**

### ⚖️ Docker vs Kubernetes

| Docker | Kubernetes |
|---|---|
| Containerization platform | Container orchestration platform |
| Builds and runs containers | Manages containerized workloads |
| Manages individual containers | Manages applications across clusters |
| Provides Docker Engine | Provides Cluster Management |
| Docker Compose manages multi-container applications | Kubernetes manages distributed workloads |
| Container lifecycle management | Scheduling, scaling, and self-healing |

**Note:** Docker and Kubernetes are not direct replacements for each other. Kubernetes works with container runtimes such as containerd and CRI-O.

---

## 🏗️ Understanding Kubernetes Architecture

Kubernetes uses a Cluster Architecture consisting of two major components:

1. Control Plane
2. Worker Nodes

### 1. Control Plane

The Control Plane manages the overall Kubernetes cluster and makes decisions about scheduling and maintaining the desired state of applications.

Important components:

| Component | Responsibility |
|---|---|
| kube-apiserver | Exposes the Kubernetes API |
| etcd | Stores cluster state and configuration data |
| kube-scheduler | Schedules Pods onto suitable Worker Nodes |
| kube-controller-manager | Runs controllers to maintain desired states |
| cloud-controller-manager | Integrates with supported cloud platforms |

### 2. Worker Nodes

Worker Nodes are responsible for running application workloads inside Pods.

Important components:

| Component | Responsibility |
|---|---|
| kubelet | Ensures Pods and their containers run as specified |
| kube-proxy | Implements Service networking rules when used |
| Container Runtime | Runs containers using a supported runtime |

### 🖥️ Kubernetes Cluster Architecture

```text
                  Kubernetes Cluster
                         |
             +-----------+-----------+
             |                       |
        Control Plane             Worker Nodes
             |                       |
     +-------+-------+          +----+----+
     |       |       |          |         |
 API Server etcd  Scheduler  kubelet  kube-proxy
     |       |       |          |
     +-------+-------+       Container Runtime
             |                  |
      Controller Manager       Pods
                                |
                         +------+------+
                         |             |
                       Pod 1         Pod 2
                         |             |
                      Container     Container
```

### 🔄 How Kubernetes Works

1. A user submits a deployment configuration using `kubectl`.
2. The request reaches the Kubernetes API Server.
3. The desired cluster state is stored in etcd.
4. The Scheduler selects a suitable Worker Node.
5. The kubelet communicates with the container runtime.
6. The required containers are started inside Pods.
7. Kubernetes controllers continuously monitor the cluster and work to maintain the desired state.

---

## 📦 Important Kubernetes Concepts

| Concept | Description |
|---|---|
| Cluster | Collection of Control Plane and Worker Nodes |
| Node | Machine that runs Kubernetes workloads |
| Pod | Smallest deployable unit in Kubernetes |
| Deployment | Manages stateless application Pods |
| ReplicaSet | Maintains the required number of Pod replicas |
| Service | Provides stable networking access to Pods |
| Namespace | Logical isolation of Kubernetes resources |
| ConfigMap | Stores non-confidential configuration |
| Secret | Stores sensitive configuration data |
| Volume | Provides storage to Pods |
| PersistentVolume | Cluster storage resource |
| PersistentVolumeClaim | Request for persistent storage |
| Ingress | Manages external HTTP/HTTPS access to Services |

---

## 🛠️ Installation & Command References

Before starting the practical lessons, Kubernetes tools and a suitable cluster environment must be installed and configured.

### 1. Kubernetes Installation Guide

📦 **Kubernetes Installation – Step-by-Step Commands**

[DevOps Tools Installation – Kubernates.md](https://github.com/byteAlok/DevOps-Tools-Installation-Commands/blob/main/DevOps%20%26%20Infrastructure/Kubernates.md)

Contains Kubernetes installation instructions, setup commands, and configuration steps.

### 2. Kubernetes Command Handbook

⌨️ **Kubernetes – Essential Command Reference**

[System Command Handbook – kubernetes.md](https://github.com/byteAlok/System-Command-Handbook/blob/main/kubernetes.md)

Contains approximately 20 commonly used Kubernetes commands with their syntax and usage examples.

Useful for quick reference while working with Pods, Deployments, Services, Nodes, Namespaces, and other Kubernetes resources.

---

## 📚 Learning Structure

All learning materials are organized day-wise.

Each day contains a Markdown file documenting the topics covered, commands executed, YAML configurations, explanations, and practical results.

### 📂 Repository Structure

```text
Kubernetes/
│
├── README.md
│
├── Day-01-Introduction-to-Kubernetes.md
│
├── Day-02-Kubernetes-Architecture.md
│
├── Day-03-Kubernetes-Cluster-Components.md
│
├── Day-04-Kubectl-Commands.md
│
├── Day-05-Pods/
│   ├── README.md
│   └── pod.yaml
│
├── Day-06-ReplicaSets/
│   ├── README.md
│   └── replicaset.yaml
│
├── Day-07-Deployments/
│   ├── README.md
│   └── deployment.yaml
│
├── Day-08-Services/
│   ├── README.md
│   └── service.yaml
│
└── ...
```

*Note: The above structure is an example. Actual files and folders will be added as new topics are covered.*

### 📝 Documentation Naming Convention

**For theoretical topics and command-based practicals:**

```text
Day-<n>-<Topic-Name>.md
```

Examples:

```text
Day-01-Introduction-to-Kubernetes.md
Day-02-Kubernetes-Architecture.md
Day-03-Kubernetes-Cluster-Components.md
Day-04-Kubectl-Commands.md
```

**For practical topics requiring additional files:**

```text
Day-<n>-<Topic-Name>/
│
├── README.md
├── deployment.yaml
├── service.yaml
└── additional-files/
```

Example:

```text
Day-07-Deployments/
│
├── README.md
└── deployment.yaml
```

### 📄 Daily Documentation Includes

- 📖 Topic Introduction
- 🧠 Conceptual Explanation
- 🏗️ Architecture and Components
- 💻 Commands and Syntax
- 📜 YAML Manifest Examples
- 🔍 Command Execution Results
- 🧪 Hands-on Practicals
- 📌 Important Notes and Learnings

---

## 🚀 Learning Approach

This repository follows a practical, step-by-step learning approach.

1. Understand the concept and architecture.
2. Learn the required Kubernetes commands.
3. Configure and interact with the Kubernetes cluster.
4. Create and apply YAML manifests.
5. Deploy and manage containerized applications.
6. Observe and troubleshoot cluster behavior.
7. Document the learning and implementation.

The goal is not just to understand Kubernetes theoretically, but to gain practical experience in container orchestration, cluster administration, application deployment, and real-world DevOps workflows.

---

## 🔗 Useful Resources

- 📘 [Kubernetes Official Documentation](https://kubernetes.io/docs/)
- 🚀 [Kubernetes Concepts](https://kubernetes.io/docs/concepts/)
- ⌨️ [Kubectl Command Reference](https://kubernetes.io/docs/reference/kubectl/)
- 🏗️ [Kubernetes Cluster Architecture](https://kubernetes.io/docs/concepts/architecture/)
- 📦 [Kubernetes Workloads](https://kubernetes.io/docs/concepts/workloads/)
- 🔐 [Kubernetes Security](https://kubernetes.io/docs/concepts/security/)
- 🛠️ [Kubernetes Installation Guide](https://github.com/byteAlok/DevOps-Tools-Installation-Commands/blob/main/DevOps%20%26%20Infrastructure/Kubernates.md)
- ⌨️ [Kubernetes Command Handbook](https://github.com/byteAlok/System-Command-Handbook/blob/main/kubernetes.md)

---

## 👨‍💻 Author

**Alok Maurya**

- 🐙 GitHub: [@byteAlok](https://github.com/byteAlok)
- 🌐 Portfolio: [aloksde.com](https://aloksde.com)

💡 Learning | Building | Experimenting | Growing

---

⭐ If you find this repository helpful, consider giving it a star!
