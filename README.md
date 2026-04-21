 DevOps Demo Project

##  Project Title
DevOps Infrastructure for High Availability Application

---

##  Description
This project demonstrates a complete DevOps pipeline using AWS EC2, Docker, Kubernetes, and Ansible to deploy a scalable web application.

---

##  Technologies Used
- AWS EC2
- Docker
- Kubernetes
- Ansible
- Git & GitHub

---

##  Architecture
User → Load Balancer → Kubernetes Service → Pods → Docker Container  
Auto Scaling via HPA (CPU > 50%)

---

##  Features
- Containerized application using Docker
- Automated deployment using Kubernetes
- Auto scaling using HPA
- Infrastructure automation using Ansible
- Network policies for security

---

##  Deployment Steps
1. Build Docker image
2. Push to DockerHub
3. Deploy using Kubernetes YAML files
4. Expose using NodePort service
5. Configure HPA for auto scaling

---

##  Output
Application successfully running on Kubernetes cluster with high availability and scalability.

---

##  Author
Yamini
