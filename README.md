 DevOps Demo Project
 Project Title

DevOps Infrastructure for High Availability Web Application

Description

This project demonstrates a complete DevOps infrastructure for deploying a scalable and highly available web application using AWS, Docker, Kubernetes, and Ansible. The system ensures automation, scalability, and fault tolerance using modern DevOps practices.

Technologies Used
AWS EC2 (Infrastructure)
Docker (Containerization)
Kubernetes (Orchestration)
Ansible (Automation)
Git & GitHub (Version Control)
Linux (Ubuntu)
Architecture
User
  ↓
Load Balancer / NodePort Service
  ↓
Kubernetes Cluster
  ↓
Pods (Application Containers)
  ↓
Docker Image
 Key Features
✔ Containerized web application using Docker
✔ Kubernetes-based deployment for scalability
✔ Auto-healing and self-managed pods
✔ Horizontal Pod Autoscaling (HPA)
✔ Network policies for secure communication
✔ Infrastructure automation using Ansible
✔ High availability across multiple worker nodes
 Deployment Steps
1. Build Docker Image
docker build -t devops-demo-app:1.0 .
2. Push Image to DockerHub
docker push <dockerhub-username>/devops-demo-app:1.0
3. Deploy to Kubernetes
kubectl apply -f deployment.yml
4. Expose Application
kubectl apply -f service.yml

Access:

http://98.130.45.172:30080
5. Apply Network Policy
kubectl apply -f network-policy.yml
6. Enable Auto Scaling (HPA)
kubectl autoscale deployment devops-demo --cpu-percent=50 --min=1 --max=5
 Output
Application successfully deployed on Kubernetes cluster
Accessible via NodePort service
Auto scaling enabled using HPA
Secure communication using network policies
Highly available multi-node architecture

 Author
yamini
