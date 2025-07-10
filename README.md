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
```
- This maps container port 3000 to EC2's port 3000
- You should see output like a container ID
  
### 📦 Image Size
```bash
docker images
```

<img width="1671" height="233" alt="Screenshot 2025-07-09 221710" src="https://github.com/user-attachments/assets/c2d61821-f288-4f45-ae74-bf58625b95cf" />


🌐 Access in Browser  

Visit the app in your browser :

```bash
http://<your-ec2-public-ip>:3000
```

You should see : Hello from  Docker Multi-stage build!

✅ Make sure port 3000 is open in the EC2 security group.


<img width="1908" height="882" alt="Screenshot 2025-07-09 221311" src="https://github.com/user-attachments/assets/fb85d9a5-4a91-4358-9fc5-5c17bbd2a01b" />

### 🔹 5. Build & Run Multi-Stage Optimized Image
#### 🏗️ Build Optimized Image

```bash
docker build -t myapp-optimized .
```
### ▶️ Run Optimized Container

```bash
docker run -d -p 3001:3000 myapp-optimized
```

This maps EC2 port 3001 to the container’s port 3000.


### 📦 Optimized Image Size
```bash
docker images
```

<img width="1881" height="299" alt="Screenshot 2025-07-09 223130" src="https://github.com/user-attachments/assets/0e794953-d210-496f-ad4b-d8c3a1523df2" />


### 📊 Image Size Comparison

| Build Type         | Image Name        | Size     |
|--------------------|-------------------|----------|
| Basic Docker Build | `myapp-basic`     | ~1.09 GB |
| Multi-Stage Build  | `myapp-optimized` | ~192 MB  |

> 🧠 Multi-stage builds help reduce image size drastically by removing build-time dependencies.

 ---

### 💡 Key Learnings

- How to use Docker to containerize a Node.js app
- Difference between a regular Docker build and a multi-stage build
- How multi-stage builds reduce final image size and improve security
- How to expose containers using ports and access them from EC2


---

  
