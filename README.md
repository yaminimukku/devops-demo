DevOps Course-End Project 1 Documentation
Project Title

Infra Optimization – DevOps Infrastructure for High Availability Application

 1. Project Overview

This project focuses on designing and implementing a highly available and scalable DevOps infrastructure for an e-commerce-like application (EasyPay). The system is deployed on AWS EC2 using Kubernetes, Docker, and supporting DevOps tools to ensure automation, reliability, and fault tolerance.

The main objective is to eliminate downtime issues and ensure continuous availability of the application through container orchestration and clustering.

 2. Objectives
Build a high availability Kubernetes cluster on AWS EC2
Deploy a containerized web application
Automate application deployment using Kubernetes
Implement load balancing and service exposure
Configure network security using Network Policies
Enable auto scaling using HPA
Take ETCD snapshot for backup and recovery
 3. Technologies Used
AWS EC2 (Infrastructure)
Ubuntu 24.04
Docker (Containerization)
Kubernetes (Cluster Orchestration)
kubeadm (Cluster Setup)
Flannel (CNI Networking)
kubectl (Cluster Management)
ETCD (Cluster Database Backup)
 4. System Architecture
User
  ↓
NodePort Service (Kubernetes)
  ↓
Deployment (Pods)
  ↓
Docker Container (Web App)
  ↓
Worker Nodes (EC2 Instances)
  ↓
Kubernetes Cluster (Master + Workers)
5. Infrastructure Setup
EC2 Instances Used:
1 Master Node (Control Plane)
2 Worker Nodes
Kubernetes Cluster:
Version: v1.29
Container Runtime: containerd
CNI Plugin: Flannel
6. Implementation Steps
Step 1: EC2 Instance Setup
Created 3 EC2 instances (1 master, 2 workers)
Configured security groups to allow Kubernetes ports
Step 2: Install Kubernetes Components

Installed on all nodes:

kubeadm
kubelet
kubectl
containerd
Step 3: Initialize Master Node
kubeadm init

Configured kubeconfig:

mkdir -p $HOME/.kube
cp /etc/kubernetes/admin.conf $HOME/.kube/config
Step 4: Install CNI (Flannel)
kubectl apply -f kube-flannel.yml
Step 5: Join Worker Nodes

Executed join command:

kubeadm join <master-ip>:6443 --token <token> --discovery-token-ca-cert-hash <hash>
Step 6: Deploy Application
kubectl apply -f deployment.yml
Step 7: Expose Application Service
kubectl apply -f service.yml

Service Type:

NodePort

Access URL:

http://98.130.45.172:30080
Step 8: Network Security Policy

Applied network policy to control pod communication:

kubectl apply -f network-policy.yml
Step 9: ETCD Snapshot Backup

Created backup of cluster state:

etcdctl snapshot save snapshot.db

✔ Snapshot File: snapshot.db (2.1MB)

7. Kubernetes Verification
kubectl get nodes
kubectl get pods -A
kubectl get svc
kubectl get hpa
kubectl get networkpolicy
8. Application Output
Application successfully deployed on Kubernetes cluster
Accessible via NodePort service
Pods distributed across worker nodes
Load balanced traffic across containers
High availability ensured through multi-node setup
9. Security Features
Network Policies implemented for controlled traffic flow
Kubernetes RBAC-ready environment
Secure ETCD snapshot backup
10. Key Deliverables
Kubernetes cluster setup on AWS EC2
Containerized application deployment
Service exposure via NodePort
Network policy implementation
ETCD snapshot backup file
Auto scaling configuration (HPA)


Final Status

✔ Cluster Created Successfully
✔ Application Deployed
✔ Service Exposed
✔ Network Policy Applied
✔ ETCD Snapshot Taken
✔ HPA Configured


 Author

Yamini