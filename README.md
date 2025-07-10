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
#### ✅ (Optional) Run Docker Without `sudo`
To avoid using `sudo` with every Docker command, add your user to the Docker group:
```bash
sudo usermod -aG docker $USER
```
- Now log out and log back in to apply the changes
- Then SSH again 

### 🔹 2. Setup Project Directory

You can either clone from GitHub or create the files manually on your EC2 instance.
### 🔹 3. Build Docker Images
Once your project files are in place, build the Docker images using the provided Dockerfiles.
#### 🧱 Build Basic Image
```bash
docker build -t myapp-basic .
```

> ✅ Build completed successfully — see below :

<img width="1874" height="849" alt="Screenshot 2025-07-09 205750" src="https://github.com/user-attachments/assets/8f7af62a-0da2-45d0-b9f5-e86642f592ef" />



### 🔹 4. Run the Docker Containers
After building the image, run the container using the following command :
```bash
docker run -d -p 3000:3000 myapp-basic




  
