#   Docker Multi-Stage Build Demo – Node.js App
This project demonstrates the use of **Docker Multi-Stage Builds** to optimize image size and prepare a Node.js application for efficient production deployment.
## 🎯 Project Goals
This project demonstrates the use of **Docker Multi-Stage Builds** to optimize Docker images by separating the **build environment** from the **runtime environment**. The goal is to:

- Compare a **Basic Dockerfile** vs a **Multi-Stage Dockerfile**
- Reduce final image size and improve deployment efficiency
- Understand and apply production-ready container practices
- Run both containers on AWS EC2 and test real-time accessibility

---
## 🛠️ Tools and Services Used

| Tool/Service       | Purpose                                   |
|--------------------|--------------------------------------------|
| **Node.js**        | Runtime environment for the web app       |
| **Docker**         | Containerization of app                   |
| **Dockerfile**     | To define how the app is built and run    |
| **Multi-Stage Build** | To optimize image size and remove unnecessary layers |
| **AWS EC2 (Ubuntu)** | Cloud instance to host and test the containers |
| **Git & GitHub**   | Version control and sharing the project   |

---
## 🧑‍💻 Step-by-Step Implementation
### 🔹 1. Setup EC2 & Install Docker
#### ✅ Launch EC2 Instance
- OS : Ubuntu (e.g., Ubuntu 20.04)
- Add Security Group Inbound Rules:
  - Port 22 (SSH)
  - Port 3000 (for basic container)
  - Port 3001 (for optimized container)
  - #### ✅ SSH into EC2
```bash
ssh -i your-key.pem ubuntu@<your-ec2-public-ip>
```
#### ✅ Install Docker
```bash
sudo apt update
sudo apt install docker.io -y
sudo systemctl start docker
sudo systemctl enable docker
docker --version
```

  
