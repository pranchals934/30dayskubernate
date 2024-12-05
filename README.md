# 30dayskubernate
name: Broken link checker
on:
  # can be used to run workflow manually
  workflow_dispatch:
  schedule:
    # Automatically run on every sunday of the month
    - cron:  '0 1 * * 0'
jobs:      
    broken-link-check:
        runs-on: ubuntu-latest
        timeout-minutes: 30
        steps:
        - name: Check out repository
          uses: actions/checkout@v4.1.0
    
        - name: Link Checker
          id: lychee
          uses: lycheeverse/lychee-action@v1.8.0
          with:
            fail: true
          env:
            GITHUB_TOKEN: ${{secrets.GITHUB_TOKEN}} 
‎.lycheeignore
+2
Original file line number	Diff line number	Diff line change
@@ -0,0 +1,2 @@
# Ignore file for broken link checker action, anything added here will be ignored lycheeverse/lychee-action@.*
^https?://www.linkedin.com/in/.*$
‎Day08/README.md
+1
-1


Original file line number	Diff line number	Diff line change
@@ -31,6 +31,6 @@ By the end of today, you will:
- [Kubernetes- Replication Sets and Controller in Hindi](https://youtu.be/dQSQELeC2A4?si=-1wmFtf-1JQU6B6M)
- [Kubernetes- Replication Sets and Controller in English](https://youtu.be/D15dzWkor28?si=UIynIMYpSWDZgCkz)

Understanding ReplicationSets and controllers is essential for ensuring the availability and scalability of your applications in Kubernetes. Tomorrow, we'll explore Kubernetes Jobs for batch task management.
Understanding ReplicationSets and controllers is essential for ensuring the availability and scalability of your applications in Kubernetes. Tomorrow, we'll explore Deployment Object in Kubernetes.

[← Previous Day](../Day07/README.md) | [Next Day →](../Day09/README.md)
‎Day09/README.md
+32
-16


Original file line number	Diff line number	Diff line change
@@ -1,33 +1,49 @@
# Day 09: Kubernetes Jobs
# Day 09: Deployment Object in Kubernetes
[![LinkedIn](https://img.shields.io/badge/Connect%20with%20me%20on-LinkedIn-blue.svg)](https://www.linkedin.com/in/aman-devops/)
[![GitHub](https://img.shields.io/github/stars/AmanPathak-DevOps.svg?style=social)](https://github.com/AmanPathak-DevOps)
[![GitHub stars](https://img.shields.io/github/stars/AmanPathak-DevOps/30DaysOfKubernetes)](https://github.com/AmanPathak-DevOps/30DaysOfKubernetes/stargazers)

Welcome to Day 09 of the Kubernetes 30-Day Learning Challenge! 🚀 Today, we'll explore Kubernetes Jobs for batch task management.
Welcome to Day 9 of the #30DaysOfKubernetes challenge! Today, we're diving into the powerful world of Deployment Objects in Kubernetes. 🚀

## 📋 Learning Objectives
## Learning Objectives

By the end of today, you will:
- **Kubernetes Jobs**: Understand the concept of Kubernetes Jobs for running batch tasks in a cluster.

## 🚀 Let's Get Started
- **Understand Kubernetes**: Grasp the core concepts and principles of Kubernetes.

### Task 1: Kubernetes Jobs
- Dive into the [Kubernetes Jobs documentation](https://kubernetes.io/docs/concepts/workloads/controllers/job/) to grasp the concept and usage of Jobs.
- Learn how to create and manage Jobs in a Kubernetes cluster.
- **Explore Container Orchestration**: Discover the role of container orchestration in modern applications.

### Task 2: Running Batch Tasks
- Experiment with running batch tasks using Kubernetes Jobs in your local cluster.
- Observe how Jobs ensure the successful completion of tasks.
- **Recognize Kubernetes Use Cases**: Learn when and why Kubernetes is the preferred choice for managing containers.

### Task 3: Suggested Project
- Create a simple batch task using Kubernetes Jobs. You can simulate tasks like data processing or batch computations.
## Why Deployments Matter
- **Robust Scaling**: Deployments allow for dynamic scaling, ensuring your applications meet varying demand with ease.
- **Effortless Updates**: Manage application updates seamlessly, rolling out new versions without downtime.
- **Reliable Rollbacks**: If a new version encounters issues, Deployments make it simple to revert to a stable state.
- **Declarative Configuration**: Define the desired state of your application, and let Kubernetes handle the rest.
## Use Cases
Deployments are invaluable for:
1. **Scaling Applications**: Scale up or down as needed, ensuring your application can handle traffic spikes.
2. **Efficient Updates**: Implement rolling updates to keep your applications current and bug-free.
3. **Quick Rollbacks**: Swiftly revert to a previous version when issues arise during an update.
4. **Easy Rollout**: Gradually replace old Pods with new ones, ensuring a smooth transition.

## 🌐 Additional Resources

- [Kubernetes Official Documentation - Jobs](https://kubernetes.io/docs/concepts/workloads/controllers/job/): Detailed information on Kubernetes Jobs.
- [Kubernetes Job, Init Container and Pod lifecycle in Hindi](https://youtu.be/BqHAoaXbz1A?si=Fd-mU-jNzaM2Fb7G)
- [Deployment Object in Kubernetes Official Documentation](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/)
- [Kubernetes on GitHub](https://github.com/kubernetes/kubernetes)
- [Deployment Object in Hindi](https://youtu.be/t3z-vkk_T6g?si=xl5QfPPWAYnjML77)
- [Kubernetes in English](https://youtu.be/lVKLkyuRWCY?si=HMj99wyAKIxnggKs)

Kubernetes Jobs are essential for managing batch workloads efficiently. Tomorrow, we'll explore the role of Init Containers in Kubernetes.
Understanding and handsOn for Deployment object in kubernetes really helpful to deploy your application more awesome. Tomorrow, we'll Setup Kubernetes Master and Worker Nodes Using Kubeadm.

[← Previous Day](../Day08/README.md) | [Next Day →](../Day10/README.md)
‎Day10/README.md
+18
-13


Original file line number	Diff line number	Diff line change
@@ -1,32 +1,37 @@
# Day 10: Init Containers
# Day 10: Setup Kubernetes Master and Worker Nodes Using Kubeadm
[![LinkedIn](https://img.shields.io/badge/Connect%20with%20me%20on-LinkedIn-blue.svg)](https://www.linkedin.com/in/aman-devops/)
[![GitHub](https://img.shields.io/github/stars/AmanPathak-DevOps.svg?style=social)](https://github.com/AmanPathak-DevOps)
[![GitHub stars](https://img.shields.io/github/stars/AmanPathak-DevOps/30DaysOfKubernetes)](https://github.com/AmanPathak-DevOps/30DaysOfKubernetes/stargazers)

Welcome to Day 10 of the Kubernetes 30-Day Learning Challenge! 🚀 Today, you'll understand the role of Init Containers in preparing application containers.
Welcome to Day 10 of the Kubernetes 30-Day Learning Challenge! 🚀 Today, you'll learn how to set up Kubernetes master and worker nodes on a cloud provider like AWS.

## 📋 Learning Objectives

By the end of today, you will:
- **Init Containers**: Learn about Init Containers and their significance in containerized applications.
- **Kubernetes Cluster Setup**: Understand the process of setting up Kubernetes master and worker nodes on a cloud provider.

## 🚀 Let's Get Started

### Task 1: Init Containers
- Explore the [Kubernetes Init Containers documentation](https://kubernetes.io/docs/concepts/workloads/pods/init-containers/) to understand what Init Containers are and how they work.
- Learn how to define and use Init Containers in a Pod specification.
### Task 1: Cloud Provider Setup
- Choose a cloud provider (e.g., AWS, GCP, Azure) for your Kubernetes cluster.
- Explore the official documentation of your chosen cloud provider for Kubernetes cluster setup.

### Task 2: Use Cases
- Study real-world use cases for Init Containers. These include preparing application configuration, setting up databases, or downloading necessary files before the main application starts.
### Task 2: Kubernetes Installation
- Follow the instructions in the cloud provider's documentation to set up a Kubernetes cluster with both master and worker nodes.

### Task 3: Suggested Project
- Implement an Init Container in a Kubernetes Pod. Create a scenario where an Init Container sets up environment variables for the main application.
### Task 3: Cluster Verification
- Verify that your Kubernetes cluster is up and running. Ensure that you can interact with it using kubectl.
### Task 4: Suggested Project
- Deploy a sample application on your cloud-based Kubernetes cluster to practice managing nodes and applications in a cloud environment.

## 🌐 Additional Resources

- [Kubernetes Official Documentation - Init Containers](https://kubernetes.io/docs/concepts/workloads/pods/init-containers/): In-depth information on Kubernetes Init Containers.
- [Kubernetes Job, Init Container and Pod lifecycle in Hindi](https://youtu.be/BqHAoaXbz1A?si=Fd-mU-jNzaM2Fb7G)
- [Kubernetes Documentation - Getting Started Guides](https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/create-cluster-kubeadm/): Official Kubernetes documentation with guides for various cloud providers.
- [Kubernetes Master and Worker Nodes Setup in Hindi](https://youtu.be/ftrAFHL6w2c?si=W1aW8RPRp6--bdu6)
- [Kubernetes Master and Worker Nodes Setup in English](https://youtu.be/6_i1hXXviHw?si=GSknYK-RoLSiXvJz)
- [Kubernetes Master and Worker Nodes Setup in English](https://youtu.be/gsQFa3bIHE0?si=NBm00879IyoyID1J)

Init Containers play a crucial role in ensuring that your application containers start with the necessary prerequisites. Tomorrow, we'll dive into the Pod lifecycle in Kubernetes.
Setting up Kubernetes master and worker nodes on a cloud provider is a crucial step in preparing your cluster for real-world applications. Tomorrow, we'll delve into advanced Kubernetes networking concepts.

[← Previous Day](../Day09/README.md) | [Next Day →](../Day11/README.md)
‎Day11/README.md
+17
-14


Original file line number	Diff line number	Diff line change
@@ -1,33 +1,36 @@
# Day 11: Pod Lifecycle
# Day 11: Advanced Kubernetes Networking
[![LinkedIn](https://img.shields.io/badge/Connect%20with%20me%20on-LinkedIn-blue.svg)](https://www.linkedin.com/in/aman-devops/)
[![GitHub](https://img.shields.io/github/stars/AmanPathak-DevOps.svg?style=social)](https://github.com/AmanPathak-DevOps)
[![GitHub stars](https://img.shields.io/github/stars/AmanPathak-DevOps/30DaysOfKubernetes)](https://github.com/AmanPathak-DevOps/30DaysOfKubernetes/stargazers)

Welcome to Day 11 of the Kubernetes 30-Day Learning Challenge! 🚀 Today, you'll dive into the lifecycle of Kubernetes Pods.
Welcome to Day 11 of the Kubernetes 30-Day Learning Challenge! 🚀 Today, we'll delve into advanced Kubernetes networking concepts and solutions, including Container Network Interface (CNI) and Calico.

## 📋 Learning Objectives

By the end of today, you will:
- **Pod Lifecycle**: Understand the various phases and states in the lifecycle of Kubernetes Pods.
- **CNI and Calico**: Understand advanced Kubernetes networking concepts.
- **Use Cases**: Explore real-world use cases for advanced networking solutions.

## 🚀 Let's Get Started

### Task 1: Pod Lifecycle
- Explore the [Kubernetes Pod Lifecycle documentation](https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle/) to learn about the different phases Pods go through, from creation to termination.
- Understand the significance of each phase and how Pods handle failures and restarts.
### Task 1: CNI and Calico Overview
- Research and read about Container Network Interface (CNI) and [Calico](https://docs.tigera.io/calico/latest/about/), a popular networking solution for Kubernetes.

### Task 2: Pod States
- Study the various states that a Pod can be in, including Pending, Running, Succeeded, Failed, and Unknown.
- Explore how these states affect application availability and troubleshooting.
### Task 2: Setting Up Calico
- If you have a Kubernetes cluster, try setting up Calico as your network plugin. Alternatively, use Minikube or another cluster for experimentation.

### Task 3: Suggested Project
- Create a Pod with a simple application and experiment with different scenarios to observe the Pod's lifecycle, such as crashing the application container.
### Task 3: Exploring Advanced Networking
- Explore advanced networking topics, such as network policies, security, and observability with Calico.
### Task 4: Suggested Project
- Implement network policies using Calico in your Kubernetes cluster to secure communication between pods.

## 🌐 Additional Resources

- [Kubernetes Official Documentation - Pod Lifecycle](https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle/): Detailed information on Kubernetes Pod Lifecycle.
- [Kubernetes Job, Init Container and Pod lifecycle in Hindi](https://youtu.be/BqHAoaXbz1A?si=Fd-mU-jNzaM2Fb7G)
- [Calico Documentation](https://docs.tigera.io/calico/latest/about/): In-depth information on Calico and Kubernetes networking.
- [Kubernetes Networking](https://youtu.be/vOo__3GqyxM?si=_r7Li9GWqTeGRHkg)
- [Kubernetes- Networing in Hindi](https://youtu.be/J2sUlm2cwQk?si=9JNS6nPo6kuzZ6UR)

Understanding the Pod lifecycle is essential for managing the availability and reliability of your applications in Kubernetes.
Understanding advanced networking is crucial for managing complex applications in Kubernetes. Tomorrow, we'll explore Kubernetes Services.

[← Previous Day](../Day10/README.md) | [Next Day →](../Day12/README.md)
‎Day12/README.md
+36


Original file line number	Diff line number	Diff line change
@@ -0,0 +1,36 @@
# Day 12: Kubernetes Services
[![LinkedIn](https://img.shields.io/badge/Connect%20with%20me%20on-LinkedIn-blue.svg)](https://www.linkedin.com/in/aman-devops/)
[![GitHub](https://img.shields.io/github/stars/AmanPathak-DevOps.svg?style=social)](https://github.com/AmanPathak-DevOps)
[![GitHub stars](https://img.shields.io/github/stars/AmanPathak-DevOps/30DaysOfKubernetes)](https://github.com/AmanPathak-DevOps/30DaysOfKubernetes/stargazers)
Welcome to Day 12 of the Kubernetes 30-Day Learning Challenge! 🚀 Today, you'll explore Kubernetes Services, a fundamental concept for load balancing and service discovery within your cluster.
## 📋 Learning Objectives
By the end of today, you will:
- **Kubernetes Services**: Understand different types of Kubernetes Services, including ClusterIP, NodePort, and LoadBalancer.
- **Service Discovery**: Learn how Kubernetes Services facilitate service discovery among pods.
## 🚀 Let's Get Started
### Task 1: Kubernetes Services
- Dive into the [Kubernetes Services documentation](https://kubernetes.io/docs/concepts/services-networking/service/) to grasp the concept and usage of Services.
### Task 2: Creating Services
- Create different types of Kubernetes Services (ClusterIP, NodePort, LoadBalancer) to expose your applications and observe their behavior.
### Task 3: Service Discovery
- Explore how pods within your cluster can discover and communicate with services using DNS.
### Task 4: Suggested Project
- Enhance one of your applications by setting up a Kubernetes Service to enable load balancing and service discovery.
## 🌐 Additional Resources
- [Kubernetes Official Documentation - Services](https://kubernetes.io/docs/concepts/services-networking/service/): Detailed information on Kubernetes Services.
- [Kubernetes- Services](https://youtu.be/T4Z7visMM4E?si=qYz8QVqBrHMIorL8)
- [Kubernetes- Services](https://youtu.be/5lzUpDtmWgM?si=bwr2sV8LTtqj4GLT)
Understanding Kubernetes Services is crucial for ensuring reliable communication and load balancing within your applications. Tomorrow, we'll explore Kubernetes volumes and storage.
[← Previous Day](../Day11/README.md) | [Next Day →](../Day13/README.md)
‎Day13/README.md
+42


Original file line number	Diff line number	Diff line change
@@ -0,0 +1,42 @@
# Day 13: Volumes, Persistent Volumes, and Persistent Volume Claims (PVC)
[![LinkedIn](https://img.shields.io/badge/Connect%20with%20me%20on-LinkedIn-blue.svg)](https://www.linkedin.com/in/aman-devops/)
[![GitHub](https://img.shields.io/github/stars/AmanPathak-DevOps.svg?style=social)](https://github.com/AmanPathak-DevOps)
[![GitHub stars](https://img.shields.io/github/stars/AmanPathak-DevOps/30DaysOfKubernetes)](https://github.com/AmanPathak-DevOps/30DaysOfKubernetes/stargazers)
Welcome to Day 13 of the Kubernetes 30-Day Learning Challenge! 🚀 Today, you'll gain insights into Kubernetes volumes, persistent volumes (PV), and persistent volume claims (PVC), which are essential for data storage in Kubernetes.
## 📋 Learning Objectives
By the end of today, you will:
- **Kubernetes Volumes**: Understand Kubernetes volumes and how they handle data storage for pods.
- **Persistent Volumes (PV)**: Explore the concept of Persistent Volumes and how they abstract physical storage.
- **Persistent Volume Claims (PVC)**: Learn how to request and use storage resources using Persistent Volume Claims.
## 🚀 Let's Get Started
### Task 1: Kubernetes Volumes
- Dive into the [Kubernetes Volumes documentation](https://kubernetes.io/docs/concepts/storage/volumes/) to understand how volumes provide pod-level data storage.
### Task 2: Persistent Volumes (PV)
- Explore [Kubernetes Persistent Volumes (PV)](https://kubernetes.io/docs/concepts/storage/persistent-volumes/) and learn how they abstract physical storage resources.
### Task 3: Persistent Volume Claims (PVC)
- Understand [Kubernetes Persistent Volume Claims (PVC)](https://kubernetes.io/docs/concepts/storage/persistent-volume-claims/) and how they enable pod-specific storage requests.
### Task 4: Dynamic Provisioning
- Experiment with dynamic provisioning of Persistent Volumes using storage classes in your Kubernetes cluster.
### Task 5: Suggested Project
- Enhance one of your applications by using Persistent Volume Claims to manage data storage effectively.
## 🌐 Additional Resources
- [Kubernetes Official Documentation - Volumes](https://kubernetes.io/docs/concepts/storage/volumes/): Detailed information on Kubernetes Volumes.
- [Kubernetes Official Documentation - Persistent Volumes](https://kubernetes.io/docs/concepts/storage/persistent-volumes/): Detailed information on Persistent Volumes (PV).
- [Kubernetes Official Documentation - Persistent Volume Claims](https://kubernetes.io/docs/concepts/storage/persistent-volume-claims/): Detailed information on Persistent Volume Claims (PVC).
- [Kubernetes- Volumes, Persistent Volumes and Persistent Volume Claims in English](https://youtu.be/0swOh5C3OVM?si=ADTl9-5KsmYf7-Ro)
- [Kubernetes- Volumes, Persistent Volumes and Persistent Volume Claims in Hindi](https://youtu.be/9zjGOCb-6As?si=ShwjUSYQsqV8NLP8)
Understanding Kubernetes storage concepts is crucial for managing data in your applications effectively. Tomorrow, we'll delve into ConfigMaps and Secrets.
[← Previous Day](../Day12/README.md) | [Next Day →](../Day14/README.md)
‎Day14/README.md
+41


Original file line number	Diff line number	Diff line change
@@ -0,0 +1,41 @@
# Day 14: ConfigMaps and Secrets
[![LinkedIn](https://img.shields.io/badge/Connect%20with%20me%20on-LinkedIn-blue.svg)](https://www.linkedin.com/in/aman-devops/)
[![GitHub](https://img.shields.io/github/stars/AmanPathak-DevOps.svg?style=social)](https://github.com/AmanPathak-DevOps)
[![GitHub stars](https://img.shields.io/github/stars/AmanPathak-DevOps/30DaysOfKubernetes)](https://github.com/AmanPathak-DevOps/30DaysOfKubernetes/stargazers)
Welcome to Day 14 of the Kubernetes 30-Day Learning Challenge! 🚀 Today, you'll explore ConfigMaps and Secrets, two valuable resources for managing configuration data and sensitive information in Kubernetes.
## 📋 Learning Objectives
By the end of today, you will:
- **ConfigMaps**: Understand how to use ConfigMaps to store and manage configuration data.
- **Secrets**: Learn how to work with Kubernetes Secrets to securely handle sensitive information.
## 🚀 Let's Get Started
### Task 1: ConfigMaps
- Dive into the [Kubernetes ConfigMaps documentation](https://kubernetes.io/docs/concepts/configuration/configmap/) to grasp the concept and usage of ConfigMaps.
### Task 2: Creating ConfigMaps
- Create a ConfigMap containing configuration data for one of your applications. Use it within a pod to access the configuration.
### Task 3: Secrets
- Explore [Kubernetes Secrets](https://kubernetes.io/docs/concepts/configuration/secret/) and learn how to store and access sensitive information, such as passwords or API keys.
### Task 4: Using Secrets
- Implement a Secret in your Kubernetes cluster, and modify your application to read sensitive data from it securely.
### Task 5: Suggested Project
- Enhance your existing applications by separating configuration data and sensitive information into ConfigMaps and Secrets, respectively.
## 🌐 Additional Resources
- [Kubernetes Official Documentation - ConfigMaps](https://kubernetes.io/docs/concepts/configuration/configmap/): Detailed information on ConfigMaps.
- [Kubernetes Official Documentation - Secrets](https://kubernetes.io/docs/concepts/configuration/secret/): Detailed information on Secrets.
- [Kubernetes Official Documentation - ConfigMaps and Secrets](https://youtu.be/FAnQTgr04mU?si=hr7HNw9Qkl7sfLJx)
- [Kubernetes Official Documentation - ConfigMaps](https://youtu.be/f-DqMTxs5z8?si=VeFHJHcX2nyVnUYU)
ConfigMaps and Secrets are fundamental for managing application configurations and sensitive data securely in Kubernetes. Tomorrow, we'll explore Kubernetes Jobs for batch task management.
[← Previous Day](../Day13/README.md) | [Next Day →](../Day15/README.md)
‎Day15/README.md
+33


Original file line number	Diff line number	Diff line change
@@ -0,0 +1,33 @@
# Day 15: Kubernetes Jobs
[![LinkedIn](https://img.shields.io/badge/Connect%20with%20me%20on-LinkedIn-blue.svg)](https://www.linkedin.com/in/aman-devops/)
[![GitHub](https://img.shields.io/github/stars/AmanPathak-DevOps.svg?style=social)](https://github.com/AmanPathak-DevOps)
[![GitHub stars](https://img.shields.io/github/stars/AmanPathak-DevOps/30DaysOfKubernetes)](https://github.com/AmanPathak-DevOps/30DaysOfKubernetes/stargazers)
Welcome to Day 15 of the Kubernetes 30-Day Learning Challenge! 🚀 Today, we'll explore Kubernetes Jobs for batch task management.
## 📋 Learning Objectives
By the end of today, you will:
- **Kubernetes Jobs**: Understand the concept of Kubernetes Jobs for running batch tasks in a cluster.
## 🚀 Let's Get Started
### Task 1: Kubernetes Jobs
- Dive into the [Kubernetes Jobs documentation](https://kubernetes.io/docs/concepts/workloads/controllers/job/) to grasp the concept and usage of Jobs.
- Learn how to create and manage Jobs in a Kubernetes cluster.
### Task 2: Running Batch Tasks
- Experiment with running batch tasks using Kubernetes Jobs in your local cluster.
- Observe how Jobs ensure the successful completion of tasks.
### Task 3: Suggested Project
- Create a simple batch task using Kubernetes Jobs. You can simulate tasks like data processing or batch computations.
## 🌐 Additional Resources
- [Kubernetes Official Documentation - Jobs](https://kubernetes.io/docs/concepts/workloads/controllers/job/): Detailed information on Kubernetes Jobs.
- [Kubernetes Job, Init Container and Pod lifecycle in Hindi](https://youtu.be/BqHAoaXbz1A?si=Fd-mU-jNzaM2Fb7G)
Kubernetes Jobs are essential for managing batch workloads efficiently. Tomorrow, we'll explore the role of Init Containers in Kubernetes.
[← Previous Day](../Day14/README.md) | [Next Day →](../Day16/README.md)
‎Day16/README.md
+32


Original file line number	Diff line number	Diff line change
@@ -0,0 +1,32 @@
# Day 16: Init Containers
[![LinkedIn](https://img.shields.io/badge/Connect%20with%20me%20on-LinkedIn-blue.svg)](https://www.linkedin.com/in/aman-devops/)
[![GitHub](https://img.shields.io/github/stars/AmanPathak-DevOps.svg?style=social)](https://github.com/AmanPathak-DevOps)
[![GitHub stars](https://img.shields.io/github/stars/AmanPathak-DevOps/30DaysOfKubernetes)](https://github.com/AmanPathak-DevOps/30DaysOfKubernetes/stargazers)
Welcome to Day 16 of the Kubernetes 30-Day Learning Challenge! 🚀 Today, you'll understand the role of Init Containers in preparing application containers.
## 📋 Learning Objectives
By the end of today, you will:
- **Init Containers**: Learn about Init Containers and their significance in containerized applications.
## 🚀 Let's Get Started
### Task 1: Init Containers
- Explore the [Kubernetes Init Containers documentation](https://kubernetes.io/docs/concepts/workloads/pods/init-containers/) to understand what Init Containers are and how they work.
- Learn how to define and use Init Containers in a Pod specification.
### Task 2: Use Cases
- Study real-world use cases for Init Containers. These include preparing application configuration, setting up databases, or downloading necessary files before the main application starts.
### Task 3: Suggested Project
- Implement an Init Container in a Kubernetes Pod. Create a scenario where an Init Container sets up environment variables for the main application.
## 🌐 Additional Resources
- [Kubernetes Official Documentation - Init Containers](https://kubernetes.io/docs/concepts/workloads/pods/init-containers/): In-depth information on Kubernetes Init Containers.
- [Kubernetes Job, Init Container and Pod lifecycle in Hindi](https://youtu.be/BqHAoaXbz1A?si=Fd-mU-jNzaM2Fb7G)
Init Containers play a crucial role in ensuring that your application containers start with the necessary prerequisites. Tomorrow, we'll dive into the Pod lifecycle in Kubernetes.
[← Previous Day](../Day15/README.md) | [Next Day →](../Day17/README.md)
‎Day17/README.md
+33


Original file line number	Diff line number	Diff line change
@@ -0,0 +1,33 @@
# Day 17: Pod Lifecycle
[![LinkedIn](https://img.shields.io/badge/Connect%20with%20me%20on-LinkedIn-blue.svg)](https://www.linkedin.com/in/aman-devops/)
[![GitHub](https://img.shields.io/github/stars/AmanPathak-DevOps.svg?style=social)](https://github.com/AmanPathak-DevOps)
[![GitHub stars](https://img.shields.io/github/stars/AmanPathak-DevOps/30DaysOfKubernetes)](https://github.com/AmanPathak-DevOps/30DaysOfKubernetes/stargazers)
Welcome to Day 17 of the Kubernetes 30-Day Learning Challenge! 🚀 Today, you'll dive into the lifecycle of Kubernetes Pods.
## 📋 Learning Objectives
By the end of today, you will:
- **Pod Lifecycle**: Understand the various phases and states in the lifecycle of Kubernetes Pods.
## 🚀 Let's Get Started
### Task 1: Pod Lifecycle
- Explore the [Kubernetes Pod Lifecycle documentation](https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle/) to learn about the different phases Pods go through, from creation to termination.
- Understand the significance of each phase and how Pods handle failures and restarts.
### Task 2: Pod States
- Study the various states that a Pod can be in, including Pending, Running, Succeeded, Failed, and Unknown.
- Explore how these states affect application availability and troubleshooting.
### Task 3: Suggested Project
- Create a Pod with a simple application and experiment with different scenarios to observe the Pod's lifecycle, such as crashing the application container.
## 🌐 Additional Resources
- [Kubernetes Official Documentation - Pod Lifecycle](https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle/): Detailed information on Kubernetes Pod Lifecycle.
- [Kubernetes Job, Init Container and Pod lifecycle in Hindi](https://youtu.be/BqHAoaXbz1A?si=Fd-mU-jNzaM2Fb7G)
Understanding the Pod lifecycle is essential for managing the availability and reliability of your applications in Kubernetes. Tomorrow, we'll explore Kubernetes namespaces and resource quotas.
[← Previous Day](../Day16/README.md) | [Next Day →](../Day18/README.md)
‎Day18/README.md
+35


Original file line number	Diff line number	Diff line change
@@ -0,0 +1,35 @@
# Day 18: Resource Quotas and Namespaces
[![LinkedIn](https://img.shields.io/badge/Connect%20with%20me%20on-LinkedIn-blue.svg)](https://www.linkedin.com/in/aman-devops/)
[![GitHub](https://img.shields.io/github/stars/AmanPathak-DevOps.svg?style=social)](https://github.com/AmanPathak-DevOps)
[![GitHub stars](https://img.shields.io/github/stars/AmanPathak-DevOps/30DaysOfKubernetes)](https://github.com/AmanPathak-DevOps/30DaysOfKubernetes/stargazers)
Welcome to Day 18 of the Kubernetes 30-Day Learning Challenge! 🚀 Today, you'll delve into Kubernetes namespaces and learn how to implement resource quotas for better cluster management.
## 📋 Learning Objectives
By the end of today, you will:
- **Kubernetes Namespaces**: Understand what Kubernetes namespaces are and how they provide logical isolation within a cluster.
- **ResourceQuota**: Learn how to use ResourceQuota to control and limit resource consumption in namespaces.
## 🚀 Let's Get Started
### Task 1: Kubernetes Namespaces
- Dive into the [Kubernetes Namespaces documentation](https://kubernetes.io/docs/concepts/overview/working-with-objects/namespaces/) to understand the concept and importance of namespaces.
- Create multiple namespaces in your cluster and experiment with deploying resources to different namespaces.
### Task 2: ResourceQuota
- Explore [Kubernetes ResourceQuota](https://kubernetes.io/docs/concepts/policy/resource-quotas/) to learn how to set resource limits for namespaces.
- Create a ResourceQuota for one of your namespaces, and observe how it impacts resource allocation.
### Task 3: Suggested Project
- Implement namespaces and resource quotas for an application with distinct resource requirements. Ensure that resource limits are enforced.
## 🌐 Additional Resources
- [Kubernetes Official Documentation](https://kubernetes.io/docs/home/): Detailed information on Kubernetes namespaces and ResourceQuotas.
- [Kubernetes- Namespace and Resource Quota in Hindi](https://youtu.be/OaZcXRJuOo8?si=DmZCW0LDqHGmEvFj)
- [Kubernetes- Namespace and Resource Quota in English](https://youtu.be/K3jNo4z5Jx8?si=5uONC-HwKEqSMB4g)
Understanding namespaces and resource quotas helps you manage and isolate workloads effectively within a Kubernetes cluster. Tomorrow, we'll explore strategies for scaling and performing updates in Kubernetes.
[← Previous Day](../Day17/README.md) | [Next Day →](../Day19/README.md)
‎Day19/README.md
+35


Original file line number	Diff line number	Diff line change
@@ -0,0 +1,35 @@
# Day 19: Scaling and Updates
[![LinkedIn](https://img.shields.io/badge/Connect%20with%20me%20on-LinkedIn-blue.svg)](https://www.linkedin.com/in/aman-devops/)
[![GitHub](https://img.shields.io/github/stars/AmanPathak-DevOps.svg?style=social)](https://github.com/AmanPathak-DevOps)
[![GitHub stars](https://img.shields.io/github/stars/AmanPathak-DevOps/30DaysOfKubernetes)](https://github.com/AmanPathak-DevOps/30DaysOfKubernetes/stargazers)
Welcome to Day 19 of the Kubernetes 30-Day Learning Challenge! 🚀 Today, you'll explore strategies for scaling your applications and performing rolling updates in Kubernetes.
## 📋 Learning Objectives
By the end of today, you will:
- **Scaling and Updates**: Understand how to scale your applications and perform rolling updates in Kubernetes.
## 🚀 Let's Get Started
### Task 1: Horizontal Pod Autoscaling
- Dive into [Horizontal Pod Autoscaling (HPA)](https://kubernetes.io/docs/tasks/run-application/horizontal-pod-autoscale/) to learn how Kubernetes can automatically adjust the number of replica Pods based on resource usage.
### Task 2: Manual Scaling
- Experiment with manually scaling your application by increasing or decreasing the number of replica Pods using `kubectl`.
### Task 3: Rolling Updates
- Explore [Kubernetes Rolling Updates](https://kubernetes.io/docs/tutorials/stateful-application/basic-stateful-set/#updating-pods) to understand how to update your application without causing downtime.
### Task 4: Suggested Project
- Take an existing application you deployed on Day 11 and perform a rolling update with a new version of the application.
## 🌐 Additional Resources
- [Kubernetes Official Documentation - Horizontal Pod Autoscaling](https://kubernetes.io/docs/tasks/run-application/horizontal-pod-autoscale/): Detailed information on HPA in Kubernetes.
- [Kubernetes- Horizontal Pod Autoscaling in Hindi](https://youtu.be/hm3jnETOoFo?si=OT2ay0rITn7Mhhsd)
- [Kubernetes- Horizontal Pod Autoscaling in English](https://youtu.be/uxuyPru3_Lc?si=nCKsBP7L_FlY-2GH)
Scaling and updating applications are crucial aspects of managing production-ready Kubernetes clusters. Tomorrow, we'll dive into multi-cluster management.
[← Previous Day](../Day18/README.md) | [Next Day →](../Day20/README.md)
‎Day20/README.md
+35


Original file line number	Diff line number	Diff line change
@@ -0,0 +1,35 @@
# Day 20: Multi-Cluster Management
[![LinkedIn](https://img.shields.io/badge/Connect%20with%20me%20on-LinkedIn-blue.svg)](https://www.linkedin.com/in/aman-devops/)
[![GitHub](https://img.shields.io/github/stars/AmanPathak-DevOps.svg?style=social)](https://github.com/AmanPathak-DevOps)
[![GitHub stars](https://img.shields.io/github/stars/AmanPathak-DevOps/30DaysOfKubernetes)](https://github.com/AmanPathak-DevOps/30DaysOfKubernetes/stargazers)
Welcome to Day 20 of the Kubernetes 30-Day Learning Challenge! 🚀 Today, you'll explore tools and techniques for managing multiple Kubernetes clusters efficiently.
## 📋 Learning Objectives
By the end of today, you will:
- **Multi-Cluster Strategy**: Understand the importance of multi-cluster strategies in Kubernetes.
- **Tools**: Explore tools and techniques for managing and orchestrating multiple Kubernetes clusters.
## 🚀 Let's Get Started
### Task 1: Multi-Cluster Strategies
- Learn about the benefits and use cases of managing multiple Kubernetes clusters. Explore strategies like multi-region and multi-cloud deployments.
### Task 2: Kubernetes Federation
- Dive into Kubernetes Federation and understand how it helps manage multiple clusters as a single entity.
### Task 3: Kubectl Contexts
- Explore the use of `kubectl` contexts to switch between and manage different Kubernetes clusters.
### Task 4: Suggested Project
- Set up multiple Kubernetes clusters in different regions or cloud providers and experiment with managing them using `kubectl` contexts.
## 🌐 Additional Resources
- [Kubernetes Official Documentation - Federation](https://kubernetes.io/docs/concepts/cluster-administration/federation/): Detailed information on Kubernetes Federation.
- [Kubernetes- MultiCluster Management](https://youtu.be/pohOtvPu_3c?si=d5AqQAsGib3wzSQB)
Managing multiple Kubernetes clusters is essential for scaling your applications and ensuring high availability. Tomorrow, we'll dive into Ingress and Network Policies.
[← Previous Day](../Day19/README.md) | [Next Day →](../Day21/README.md)
‎Day21/README.md
+40


Original file line number	Diff line number	Diff line change
@@ -0,0 +1,40 @@
# Day 21: Ingress and Network Policies
[![LinkedIn](https://img.shields.io/badge/Connect%20with%20me%20on-LinkedIn-blue.svg)](https://www.linkedin.com/in/aman-devops/)
[![GitHub](https://img.shields.io/github/stars/AmanPathak-DevOps.svg?style=social)](https://github.com/AmanPathak-DevOps)
[![GitHub stars](https://img.shields.io/github/stars/AmanPathak-DevOps/30DaysOfKubernetes)](https://github.com/AmanPathak-DevOps/30DaysOfKubernetes/stargazers)
Welcome to Day 21 of the Kubernetes 30-Day Learning Challenge! 🚀 Today, you'll dive into Ingress and Network Policies, essential components for managing external access to services and controlling network traffic within your Kubernetes cluster.
## 📋 Learning Objectives
By the end of today, you will:
- **Ingress Controllers**: Understand Ingress controllers and how they enable external access to services.
- **Network Policies**: Learn about Network Policies and their role in securing and controlling network traffic.
## 🚀 Let's Get Started
### Task 1: Ingress Controllers
- Explore the [Kubernetes Ingress documentation](https://kubernetes.io/docs/concepts/services-networking/ingress/) to understand Ingress controllers and how to set them up.
### Task 2: Setting Up Ingress
- Create an Ingress resource for one of your services to allow external access. Test and verify the setup.
### Task 3: Network Policies
- Dive into [Kubernetes Network Policies](https://kubernetes.io/docs/concepts/services-networking/network-policies/) and learn how to define policies to control traffic between pods.
### Task 4: Implementing Network Policies
- Create a Network Policy that restricts network traffic between selected pods in your cluster.
### Task 5: Suggested Project
- Enhance the security of one of your applications by implementing Network Policies to control incoming and outgoing traffic.
## 🌐 Additional Resources
- [Kubernetes Official Documentation - Ingress](https://kubernetes.io/docs/concepts/services-networking/ingress/): Detailed information on Kubernetes Ingress.
- [Kubernetes Official Documentation - Network Policies](https://kubernetes.io/docs/concepts/services-networking/network-policies/): Detailed information on Network Policies.
- [Kubernetes- Ingress](https://youtu.be/GhZi4DxaxxE?si=sDuGK70lmJWMNyaQ)
- [Kubernetes- Ingress and Network Policies](https://youtu.be/VF4hpwG_px8?si=3BlAfJ5-r8vuNwzr)
Understanding Ingress and Network Policies is crucial for managing external access and securing your Kubernetes cluster. Tomorrow, we'll dive into advanced concepts with StatefulSets.
[← Previous Day](../Day20/README.md) | [Next Day →](../Day22/README.md)
‎Day22/README.md
+35


Original file line number	Diff line number	Diff line change
@@ -0,0 +1,35 @@
# Day 22: Exploring StatefulSets
[![LinkedIn](https://img.shields.io/badge/Connect%20with%20me%20on-LinkedIn-blue.svg)](https://www.linkedin.com/in/aman-devops/)
[![GitHub](https://img.shields.io/github/stars/AmanPathak-DevOps.svg?style=social)](https://github.com/AmanPathak-DevOps)
[![GitHub stars](https://img.shields.io/github/stars/AmanPathak-DevOps/30DaysOfKubernetes)](https://github.com/AmanPathak-DevOps/30DaysOfKubernetes/stargazers)
Welcome to Day 22 of the Kubernetes 30-Day Learning Challenge! 🚀 Today, you'll dive into StatefulSets, a crucial resource for managing stateful applications with unique identities within your Kubernetes cluster.
## 📋 Learning Objectives
By the end of today, you will:
- **StatefulSets**: Understand what StatefulSets are and how they differ from Deployments.
- **Use Cases**: Explore real-world use cases where StatefulSets are the ideal choice.
## 🚀 Let's Get Started
### Task 1: Understanding StatefulSets
- Read the [Kubernetes StatefulSets documentation](https://kubernetes.io/docs/concepts/workloads/controllers/statefulset/) to gain a deep understanding of StatefulSets.
### Task 2: Deploying StatefulSets
- Create a StatefulSet for a stateful application within your Kubernetes cluster. Observe how it manages unique identities for pods.
### Task 3: Real-World Use Cases
- Research and identify scenarios where StatefulSets are the preferred choice for managing applications.
### Task 4: Suggested Project
- Apply StatefulSets to one of your projects where you need to manage stateful applications with unique identities.
## 🌐 Additional Resources
- [Kubernetes Official Documentation - StatefulSets](https://kubernetes.io/docs/concepts/workloads/controllers/statefulset/): Detailed information on StatefulSets.
- [Kubernetes- StatfulSets](https://youtu.be/pPQKAR1pA9U?si=zX9bc4FO2EyCKxDM)
Understanding StatefulSets is crucial for managing stateful applications effectively. Tomorrow, we'll continue exploring StatefulSets and learn about DaemonSets.
[← Previous Day](../Day21/README.md) | [Next Day →](../Day23/README.md)
‎Day23/README.md
+36


Original file line number	Diff line number	Diff line change
@@ -0,0 +1,36 @@
# Day 23: StatefulSets and DaemonSets
[![LinkedIn](https://img.shields.io/badge/Connect%20with%20me%20on-LinkedIn-blue.svg)](https://www.linkedin.com/in/aman-devops/)
[![GitHub](https://img.shields.io/github/stars/AmanPathak-DevOps.svg?style=social)](https://github.com/AmanPathak-DevOps)
[![GitHub stars](https://img.shields.io/github/stars/AmanPathak-DevOps/30DaysOfKubernetes)](https://github.com/AmanPathak-DevOps/30DaysOfKubernetes/stargazers)
Welcome to Day 23 of the Kubernetes 30-Day Learning Challenge! 🚀 Today, you'll continue your exploration of StatefulSets and learn about DaemonSets, which are used for running a copy of a Pod on every node in the cluster.
## 📋 Learning Objectives
By the end of today, you will:
- **DaemonSets**: Understand what DaemonSets are and when to use them.
- **Comparing StatefulSets and DaemonSets**: Explore the differences between StatefulSets and DaemonSets.
## 🚀 Let's Get Started
### Task 1: DaemonSets Overview
- Explore the [Kubernetes DaemonSets documentation](https://kubernetes.io/docs/concepts/workloads/controllers/daemonset/) to understand the role of DaemonSets in Kubernetes.
### Task 2: Deploying DaemonSets
- Create a DaemonSet within your Kubernetes cluster to run a copy of a Pod on every node. Observe its behavior.
### Task 3: StatefulSets vs. DaemonSets
- Compare and contrast the use cases for StatefulSets and DaemonSets. When would you choose one over the other?
### Task 4: Suggested Project
- Apply DaemonSets to a scenario in which you need a Pod to run on every node, such as a monitoring agent or a log collector.
## 🌐 Additional Resources
- [Kubernetes Official Documentation - DaemonSets](https://kubernetes.io/docs/concepts/workloads/controllers/daemonset/): Detailed information on DaemonSets.
- [Kubernetes- DaemonSets and StatefulSets](https://youtu.be/Vrxr-7rjkvM?si=FBLclw8sYXiiw-3C)
- [Kubernetes- DaemonSets](https://youtu.be/cdY67JqGbIc?si=sVPoahOieP2bnYrK)
Understanding StatefulsSets and DaemonSets which helps to save time. Tomorrow, we'll explore Kubernetes garbage collection.
[← Previous Day](../Day22/README.md) | [Next Day →](../Day24/README.md)
‎Day24/README.md
+33


Original file line number	Diff line number	Diff line change
@@ -0,0 +1,33 @@
# Day 24: Kubernetes Garbage Collection
[![LinkedIn](https://img.shields.io/badge/Connect%20with%20me%20on-LinkedIn-blue.svg)](https://www.linkedin.com/in/aman-devops/)
[![GitHub](https://img.shields.io/github/stars/AmanPathak-DevOps.svg?style=social)](https://github.com/AmanPathak-DevOps)
[![GitHub stars](https://img.shields.io/github/stars/AmanPathak-DevOps/30DaysOfKubernetes)](https://github.com/AmanPathak-DevOps/30DaysOfKubernetes/stargazers)
Welcome to Day 24 of the Kubernetes 30-Day Learning Challenge! 🚀 Today, you'll learn about Kubernetes Garbage Collection mechanisms for resource management.
## 📋 Learning Objectives
By the end of today, you will:
- **Kubernetes Garbage Collection**: Understand the principles of Kubernetes Garbage Collection for efficient resource utilization.
## 🚀 Let's Get Started
### Task 1: Explore Kubernetes Garbage Collection
- Dive into the [Kubernetes Garbage Collection](https://kubernetes.io/docs/concepts/workloads/controllers/garbage-collection/) documentation to grasp the concept and importance of resource cleanup.
- Learn how Kubernetes automates the removal of unused resources.
### Task 2: Cleanup Strategies
- Explore different cleanup strategies in Kubernetes, including the OrphanDependents and OwnerReferences concepts.
- Understand how these strategies help maintain a clean cluster.
### Task 3: Suggested Project
- Implement a Garbage Collection strategy in your local Kubernetes cluster. Experiment with creating and deleting resources to see the cleanup process in action.
## 🌐 Additional Resources
- [Kubernetes Official Documentation - Garbage Collection](https://kubernetes.io/docs/concepts/workloads/controllers/garbage-collection/): In-depth information on Kubernetes Garbage Collection.
- [Blog on Kubernetes Garbage Collection](https://medium.com/@bharatnc/kubernetes-garbage-collection-781223f03c17)
Kubernetes Garbage Collection is a vital aspect of cluster maintenance. Tomorrow, we'll dive into Kubernetes Operators.
[← Previous Day](../Day23/README.md) | [Next Day →](../Day25/README.md)
‎Day25/README.md
+35


Original file line number	Diff line number	Diff line change
@@ -0,0 +1,35 @@
# Day 25: Operators and Helm (Part 1)
[![LinkedIn](https://img.shields.io/badge/Connect%20with%20me%20on-LinkedIn-blue.svg)](https://www.linkedin.com/in/aman-devops/)
[![GitHub](https://img.shields.io/github/stars/AmanPathak-DevOps.svg?style=social)](https://github.com/AmanPathak-DevOps)
[![GitHub stars](https://img.shields.io/github/stars/AmanPathak-DevOps/30DaysOfKubernetes)](https://github.com/AmanPathak-DevOps/30DaysOfKubernetes/stargazers)
Welcome to Day 25 of the Kubernetes 30-Day Learning Challenge! 🚀 Today, you'll begin exploring Kubernetes Operators, a powerful tool for managing complex applications.
## 📋 Learning Objectives
By the end of today, you will:
- **Kubernetes Operators**: Understand the concept of Kubernetes Operators.
- **Use Cases**: Explore scenarios where Operators are beneficial.
## 🚀 Let's Get Started
### Task 1: Kubernetes Operators Overview
- Read about Kubernetes Operators and their significance in managing applications within Kubernetes clusters.
### Task 2: Operator Frameworks
- Explore Operator Frameworks such as the [Operator Framework](https://operatorframework.io/) and [Kubebuilder](https://book.kubebuilder.io/).
### Task 3: Use Cases
- Research and discover real-world use cases where Kubernetes Operators provide automation and simplification.
### Task 4: Suggested Project
- If you have a complex application or database, consider building a simple Operator to manage it.
## 🌐 Additional Resources
- [Kubernetes Operators Documentation](https://kubernetes.io/docs/concepts/extend-kubernetes/operator/): Official Kubernetes documentation on Operators.
- [Kubernetes- Operators](https://youtu.be/VAojjIYVhGk?si=fGO1eOYGkwKwoD8R)
Understanding Kubernetes Operators is a significant step toward managing intricate applications effectively. Tomorrow, we'll continue our exploration of Operators and Helm in Part 2.
[← Previous Day](../Day24/README.md) | [Next Day →](../Day26/README.md)
‎Day26/README.md
+35


Original file line number	Diff line number	Diff line change
@@ -0,0 +1,35 @@
# Day 26: Operators and Helm (Part 2)
[![LinkedIn](https://img.shields.io/badge/Connect%20with%20me%20on-LinkedIn-blue.svg)](https://www.linkedin.com/in/aman-devops/)
[![GitHub](https://img.shields.io/github/stars/AmanPathak-DevOps.svg?style=social)](https://github.com/AmanPathak-DevOps)
[![GitHub stars](https://img.shields.io/github/stars/AmanPathak-DevOps/30DaysOfKubernetes)](https://github.com/AmanPathak-DevOps/30DaysOfKubernetes/stargazers)
Welcome to Day 26 of the Kubernetes 30-Day Learning Challenge! 🚀 Today, you'll continue your exploration of Kubernetes Operators and dive into Helm for simplifying application deployments.
## 📋 Learning Objectives
By the end of today, you will:
- **Helm**: Understand what Helm is and its role in Kubernetes.
- **Kubernetes Operators**: Continue exploring Kubernetes Operators.
## 🚀 Let's Get Started
### Task 1: Helm Overview
- Explore Helm, a package manager for Kubernetes applications, by visiting the [Helm website](https://helm.sh/).
### Task 2: Helm Charts
- Learn about Helm charts, which are packages of pre-configured Kubernetes resources.
### Task 3: Helm in Action
- Use Helm to deploy a sample application or service to your Kubernetes cluster.
### Task 4: Suggested Project
- Create a Helm chart for one of your applications to simplify its deployment on Kubernetes.
## 🌐 Additional Resources
- [Helm Documentation](https://helm.sh/docs/): Comprehensive documentation for Helm.
- [Helm](https://youtu.be/-ykwb1d0DXU?si=OQrM8q4kDAfGTVkJ)
Helm is a valuable tool for managing Kubernetes applications. Tomorrow, you'll gain hands-on experience with Amazon Elastic Kubernetes Service (EKS).
[← Previous Day](../Day25/README.md) | [Next Day →](../Day27/README.md)
‎Day27/README.md
+35


Original file line number	Diff line number	Diff line change
@@ -0,0 +1,35 @@
# Day 27: Exploring Amazon EKS (Amazon Elastic Kubernetes Service)
[![LinkedIn](https://img.shields.io/badge/Connect%20with%20me%20on-LinkedIn-blue.svg)](https://www.linkedin.com/in/aman-devops/)
[![GitHub](https://img.shields.io/github/stars/AmanPathak-DevOps.svg?style=social)](https://github.com/AmanPathak-DevOps)
[![GitHub stars](https://img.shields.io/github/stars/AmanPathak-DevOps/30DaysOfKubernetes)](https://github.com/AmanPathak-DevOps/30DaysOfKubernetes/stargazers)
Welcome to Day 27 of the Kubernetes 30-Day Learning Challenge! 🚀 Today, you'll get hands-on experience with Amazon Elastic Kubernetes Service (Amazon EKS), Amazon's managed Kubernetes service.
## 📋 Learning Objectives
By the end of today, you will:
- **Amazon EKS**: Gain an understanding of Amazon EKS and its key features.
- **Practical Experience**: Set up and explore Amazon EKS to deploy and manage Kubernetes clusters.
## 🚀 Let's Get Started
### Task 1: Amazon EKS Overview
- Read about [Amazon EKS](https://aws.amazon.com/eks/) to understand its offerings and benefits.
### Task 2: Setting Up Amazon EKS
- Follow Amazon's documentation to set up an Amazon EKS cluster. Deploy a sample application if possible.
### Task 3: Exploring EKS Features
- Explore the features of Amazon EKS, such as automatic scaling, managed node groups, and integration with other AWS services.
### Task 4: Suggested Project
- Deploy one of your applications or projects on Amazon EKS to gain hands-on experience with this managed Kubernetes service.
## 🌐 Additional Resources
- [Amazon EKS Documentation](https://docs.aws.amazon.com/eks/latest/userguide/what-is-eks.html): Comprehensive information on Amazon EKS.
- [Kubernetes- Deploy Application on AWS EKS](https://youtu.be/RRCrY12VY_s?si=l5l9uozkInyGjrWK)
Exploring Amazon EKS provides valuable insights into using Kubernetes on AWS. Tomorrow, we'll continue our journey by exploring Azure Kubernetes Service (AKS).
[← Previous Day](../Day26/README.md) | [Next Day →](../Day28/README.md)
‎Day28/README.md
+35


Original file line number	Diff line number	Diff line change
@@ -0,0 +1,35 @@
# Day 28: Exploring Azure AKS (Azure Kubernetes Service)
[![LinkedIn](https://img.shields.io/badge/Connect%20with%20me%20on-LinkedIn-blue.svg)](https://www.linkedin.com/in/aman-devops/)
[![GitHub](https://img.shields.io/github/stars/AmanPathak-DevOps.svg?style=social)](https://github.com/AmanPathak-DevOps)
[![GitHub stars](https://img.shields.io/github/stars/AmanPathak-DevOps/30DaysOfKubernetes)](https://github.com/AmanPathak-DevOps/30DaysOfKubernetes/stargazers)
Welcome to Day 28 of the Kubernetes 30-Day Learning Challenge! 🚀 Today, you'll explore Azure Kubernetes Service (AKS), Microsoft's managed Kubernetes service in Azure, and its key features.
## 📋 Learning Objectives
By the end of today, you will:
- **Azure AKS**: Understand what Azure AKS is and its benefits.
- **Features**: Explore the features of Azure AKS for deploying and managing Kubernetes clusters.
## 🚀 Let's Get Started
### Task 1: Azure AKS Overview
- Visit the [Azure AKS documentation](https://azure.microsoft.com/en-us/services/kubernetes-service/) to learn about Azure AKS and its offerings.
### Task 2: Setting Up Azure AKS
- Follow the Azure documentation to set up an Azure AKS cluster. Deploy a sample application if available.
### Task 3: Exploring Azure AKS Features
- Dive into the features of Azure AKS, including auto-scaling, managed node pools, and integration with Azure services.
### Task 4: Suggested Project
- Deploy one of your applications or projects on Azure AKS to gain hands-on experience with this managed Kubernetes service.
## 🌐 Additional Resources
- [Azure AKS Documentation](https://docs.microsoft.com/en-us/azure/aks/): Detailed information on Azure AKS.
- [Deploy Application on AKS](https://youtu.be/Q0Jqy3Jp65c?si=FmdJA9BWA9vLsWfl)
Exploring Azure AKS is a valuable step in your Kubernetes journey. Tomorrow, we'll discover Google Kubernetes Engine (GKE), Google Cloud's managed Kubernetes service.
[← Previous Day](../Day27/README.md) | [Next Day →](../Day29/README.md)
‎Day29/README.md
+35


Original file line number	Diff line number	Diff line change
@@ -0,0 +1,35 @@
# Day 29: Exploring Google GKE (Google Kubernetes Engine)
[![LinkedIn](https://img.shields.io/badge/Connect%20with%20me%20on-LinkedIn-blue.svg)](https://www.linkedin.com/in/aman-devops/)
[![GitHub](https://img.shields.io/github/stars/AmanPathak-DevOps.svg?style=social)](https://github.com/AmanPathak-DevOps)
[![GitHub stars](https://img.shields.io/github/stars/AmanPathak-DevOps/30DaysOfKubernetes)](https://github.com/AmanPathak-DevOps/30DaysOfKubernetes/stargazers)
Welcome to Day 29 of the Kubernetes 30-Day Learning Challenge! 🚀 Today, you'll discover Google Kubernetes Engine (GKE), Google Cloud's managed Kubernetes service, and explore its capabilities.
## 📋 Learning Objectives
By the end of today, you will:
- **Google GKE**: Understand what Google GKE is and why it's a popular choice for Kubernetes.
- **Key Features**: Explore the key features of Google GKE for Kubernetes cluster management.
## 🚀 Let's Get Started
### Task 1: Google GKE Overview
- Explore the [Google Kubernetes Engine documentation](https://cloud.google.com/kubernetes-engine) to learn about Google GKE and its offerings.
### Task 2: Setting Up Google GKE
- Follow Google's documentation to set up a Google GKE cluster. Deploy a sample application if available.
### Task 3: Exploring Google GKE Features
- Delve into the features of Google GKE, including seamless integration with Google Cloud services, auto-upgrades, and logging.
### Task 4: Suggested Project
- Deploy one of your applications or projects on Google GKE to gain hands-on experience with this managed Kubernetes service.
## 🌐 Additional Resources
- [Google Kubernetes Engine Documentation](https://cloud.google.com/kubernetes-engine/docs): Comprehensive information on Google GKE.
- [Kubernetes- Deploy Application on GKE](https://youtu.be/jW_-KZCjsm0?si=o2Zvk6SmdAwk0ak6)
Exploring Google GKE is essential for those looking to leverage Google Cloud's ecosystem for Kubernetes workloads. Tomorrow, we'll delve into advanced Kubernetes networking concepts.
[← Previous Day](../Day28/README.md) | [Next Day →](../Day30/README.md)
‎Day30/README.md
+58


Original file line number	Diff line number	Diff line change
@@ -0,0 +1,58 @@
# Day 30: End-to-End Kubernetes Project with JFrog Artifactory
[![LinkedIn](https://img.shields.io/badge/Connect%20with%20me%20on-LinkedIn-blue.svg)](https://www.linkedin.com/in/aman-devops/)
[![GitHub](https://img.shields.io/github/stars/AmanPathak-DevOps.svg?style=social)](https://github.com/AmanPathak-DevOps)
[![GitHub stars](https://img.shields.io/github/stars/AmanPathak-DevOps/30DaysOfKubernetes)](https://github.com/AmanPathak-DevOps/30DaysOfKubernetes/stargazers)
Welcome to Day 30, the final day of the Kubernetes 30-Day Learning Challenge! 🚀 Today, we're embarking on an exciting journey to create an end-to-end project that showcases your Kubernetes skills.
## 📋 Project Overview
Today's project is all about applying what you've learned throughout this challenge to deploy a real-world application on a Kubernetes cluster. We'll use a combination of tools like Jenkins, SonarQube, ArgoCD, and JFrog Artifactory to create a streamlined CI/CD pipeline with artifact management.
## 🚀 Project Objectives
By the end of today, you will:
- **Set Up Jenkins**: Configure Jenkins for automated build and testing.
- **Implement SonarQube**: Integrate SonarQube for code quality analysis.
- **Artifact Management with JFrog Artifactory**: Utilize JFrog Artifactory for storing and managing Docker images, Helm charts, and other artifacts.
- **ArgoCD Deployment**: Set up ArgoCD for continuous delivery to your Kubernetes cluster.
- **Complete End-to-End CI/CD**: Create a complete CI/CD pipeline that includes code build, testing, code quality checks, artifact management, and automated deployment to your Kubernetes cluster.
- **Documentation**: Document your project, including setup instructions and a high-level architecture diagram.
## 🌐 Additional Resources
- [Jenkins Documentation](https://www.jenkins.io/doc/)
- [SonarQube Documentation](https://docs.sonarqube.org/latest/)
- [ArgoCD Documentation](https://argoproj.github.io/argo-cd/)
- [JFrog Artifactory Documentation](https://jfrog.com/help/r/jfrog-artifactory-documentation)
## 💡 Project Ideas
- **Containerize Your App**: If you haven't already, containerize your application using Docker.
- **Advanced Testing**: Implement advanced testing strategies, such as end-to-end testing.
- **Secrets and ConfigMaps**: Explore best practices for managing secrets and ConfigMaps in your Kubernetes deployment.
- **Multi-Environment Deployment**: Extend your project to support deployment to multiple Kubernetes environments (e.g., staging and production).
## 🚢 Let's Get Started
1. Start by setting up Jenkins, SonarQube, ArgoCD, and JFrog Artifactory. You can use the tools' official documentation for guidance.
2. Configure a Jenkins pipeline to build your application, run tests, and perform code quality checks.
3. Utilize JFrog Artifactory to store and manage Docker images, Helm charts, and other artifacts.
4. Set up ArgoCD for continuous deployment, ensuring your application is automatically deployed to your Kubernetes cluster.
5. Document your project. Include detailed setup instructions, architecture diagrams, and any challenges you faced.
## 🌐 Additional Resources(Projects)
- [Kubernetes- End to End Project1](https://youtu.be/0GgBi8yNQT4?si=7OcOCv3gJqhAIdn7)
- [Kubernetes- End to End Project2](https://youtu.be/jNPGo6A4VHc?si=e6AZjktjYs39KAZi)
## 🎉 Congratulations!
You've completed the Kubernetes 30-Day Learning Challenge! 🎉 This final project reflects the knowledge and skills you've gained over the past month. By successfully deploying a real-world application using Kubernetes and associated tools, you've demonstrated your ability to work effectively with container orchestration, continuous integration/continuous deployment, and artifact management.
Feel free to share your project, experiences, and achievements on LinkedIn or in a blog post to inspire others on their Kubernetes learning journey.
Thank you for participating in this challenge, and best of luck with your future Kubernetes endeavors!
[← Previous Day](../Day29/README.md) | [First Day →](../Day01/README.md)
