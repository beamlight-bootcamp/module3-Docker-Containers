# Container Orchestration

A container orchestration service is a tool or platform that manages the deployment, scaling, and operation of containers in a distributed computing environment. It helps automate the management of containerized applications across a cluster of machines, ensuring efficient resource utilization, high availability, and ease of scaling.

Container orchestration services, such as Amazon ECS (Elastic Container Service) or Kubernetes, are needed for several reasons:

1. Application Scaling: Orchestration services allow you to scale your application horizontally by adding or removing instances of containers based on demand. They provide automated scaling capabilities, ensuring that your application can handle increased traffic or workload without manual intervention.

2. Service Discovery and Load Balancing: Orchestration services offer built-in mechanisms for service discovery and load balancing. They automatically distribute incoming requests to containers, enabling efficient utilization of resources and improved application performance.

3. High Availability and Fault Tolerance: Orchestration platforms ensure high availability of applications by monitoring the health of containers and automatically restarting or replacing failed instances. They provide mechanisms to distribute containers across multiple nodes, mitigating the impact of hardware or software failures.

4. Resource Optimization: Orchestration services optimize resource allocation by scheduling containers based on available resources and constraints. They help prevent resource conflicts, ensuring efficient utilization of CPU, memory, and storage across the cluster.

5. Rolling Updates and Rollbacks: Container orchestration services facilitate seamless rolling updates and rollbacks of applications. They enable the deployment of new versions of containers while maintaining the availability of the application, allowing for smooth updates without downtime.

6. Service Composition and Dependencies: Orchestration platforms allow you to define complex service compositions and manage dependencies between containers. They provide mechanisms for inter-service communication, such as container networking and service discovery, enabling efficient collaboration between containers.

7. Monitoring and Logging: Orchestration services often include monitoring and logging capabilities that provide visibility into the health, performance, and behavior of containers. They allow you to collect metrics, logs, and events from containers and enable integration with monitoring and logging tools for centralized observability.

In summary, container orchestration services are essential for managing containerized applications at scale. They provide automation, scalability, fault tolerance, and resource optimization, simplifying the deployment and operation of container-based architectures in complex distributed environments.

# Popular container orchestration services

There are several popular container orchestration services available in the market. Here are some of them along with a short summary:

1. Kubernetes:
   - Kubernetes, often abbreviated as K8s, is an open-source container orchestration platform that has gained significant popularity and community support.
   - It provides features like automated scaling, service discovery, load balancing, rolling updates, and declarative configuration management.
   - Kubernetes has a robust ecosystem and works well with various cloud providers and on-premises infrastructure.

2. Amazon Elastic Container Service (ECS):
   - Amazon ECS is a fully managed container orchestration service offered by AWS.
   - It simplifies the deployment, management, and scaling of containers using a highly scalable and reliable infrastructure.
   - ECS integrates well with other AWS services, provides task definitions for defining container configurations, and offers options for running containers in Fargate or EC2 instances.

3. Docker Swarm:
   - Docker Swarm is a native clustering and orchestration solution for Docker containers.
   - It allows users to create and manage a swarm of Docker nodes, enabling the deployment and scaling of services across a cluster.
   - Docker Swarm is known for its simplicity and ease of use, making it a popular choice for smaller deployments and teams familiar with Docker.

4. Google Kubernetes Engine (GKE):
   - GKE is a managed Kubernetes service provided by Google Cloud Platform (GCP).
   - It offers a fully managed environment for deploying, managing, and scaling containerized applications using Kubernetes.
   - GKE provides features like automatic scaling, self-healing, integration with other GCP services, and simplified cluster management.

5. Microsoft Azure Kubernetes Service (AKS):
   - AKS is a managed Kubernetes service offered by Microsoft Azure.
   - It simplifies the deployment and management of containerized applications using Kubernetes, providing an optimized environment for running containers at scale.
   - AKS integrates well with other Azure services, offers automated scaling, monitoring, and seamless integration with Azure DevOps for CI/CD workflows.

6. Red Hat OpenShift:
   - OpenShift is a Kubernetes-based container platform offered by Red Hat.
   - It provides a comprehensive set of tools and features for building, deploying, and managing containerized applications.
   - OpenShift offers additional capabilities beyond vanilla Kubernetes, such as built-in CI/CD, integrated logging and monitoring, and developer-friendly features.

These are just a few examples of popular container orchestration services. Each service has its unique features, strengths, and integrations, so choosing the right one depends on specific requirements, familiarity with the platform, and existing infrastructure ecosystem.




Orchestrating your containers

- For handling deployments
- Managing these containers
- how to manage resources?
- Are containers crashed
- Remove Repilica containers

Container Orchestration Tools

Container Orchestration Tool are used for managing, scaling and deploying containers

Amazon ECS : Amazon Elastic Container Service is the container orchestration tool offered by AWS

—————————————

Elastic Container Service (ECS)

- Container Orchestration Service
- Manages the whole container lifecycle (start, schedule, load balance etc)

How does ECS work?

Run containerized application cluster on AWS

- ECS cluster contains services to manage containers
- Control plane which will manage the whole lifecycle of containers
- Where are these containers hosted?
- Which virtual machines?
- EC2 instances
- They will have docker runtime and ecs agent installed

—————————————————————

ECS with EC2 instances

- ECS hosted on EC2 instances
- manage the containers
- Still need to manage the Virtual Machine (create ec2 instances, join to ecs cluster, check whether enough resources are available)
- Manage server operation system
- Docker runtime, ECS agent
- Full access and control of our infrastructure

———————————————————————

ECS with AWS margate

- Container orchestration
- Hosting infrastructure management

Delegate infrastructure management also to aws?

- Alternative to EC2 instances

———————————————————————

how does aws margate work?

- Serverless way to launch containers
- Here’s my container with fargate
- fargate will analyze the container (how much resources: cpu, memory storage needed)
- provisions a server on demand

Advantages

- No need to provision and manage servers
- On demand
- Only the infrastructure resources need to run your containers
- pay only for what you use
- Easily scales up and down without fixed resources defined beforehand
- Pricing is based on how long the containers been running & how much capacity?

Price comparison

EC2 instance - pay for whole server

————————————————————

AWS fargate advantages

- infrastructure managed by aws
- containers managed by aws
- You only need to managed the application
- AWS garage is great but EC2 instances provide more control and flexibility

Integration with other AWS services

Whether using EC2 instances or fargate it provides integration with other ec2 serves

for example:

- cloud watch for monitoring
- elastic load balancer for load balancing
- IAM for permissions
- vpc for networking & so on
