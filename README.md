# Jenkins CI/CD Pipeline with SonarQube, Nexus, and Google Cloud Run

This project demonstrates a complete CI/CD pipeline built with **Jenkins**, **SonarQube**, **Nexus**, and **Google Cloud Platform (GCP)** services.  
It automates building, testing, analyzing, storing, and deploying a simple web application using best DevOps practices.

---

## 🚀 Overview

This is a **frontend-only web page**, originally part of a larger application but deployed here independently.  
The goal of this project is to showcase an end-to-end CI/CD setup using Jenkins integrated with quality and artifact management tools.

---

## 🧰 Tools and Technologies

- **Jenkins** – CI/CD automation server  
- **SonarQube** – Code quality and static analysis  
- **Nexus Repository** – Artifact repository for build artifacts  
- **GCP Artifact Registry** – Stores Docker images securely  
- **GCP Cloud Run** – Deploys and runs the containerized web app  
- **Docker** – Containerization for build and deployment  
- **GitHub** – Source code repository and webhook trigger for Jenkins  

---

## ⚙️ CI/CD Workflow

1. **Code Push** – Developer pushes changes to GitHub (branch: `jenkins-cicd`).  
2. **Jenkins Trigger** – Webhook triggers the Jenkins pipeline automatically.  
3. **Build Stage** – Jenkins builds the Docker image of the web app.  
4. **Code Quality Check** – SonarQube analyzes the code for bugs and vulnerabilities.  
5. **Artifact Storage** – Build artifacts are uploaded to Nexus Repository.  
6. **Docker Push** – Docker image is pushed to **GCP Artifact Registry**.  
7. **Deployment** – The image is deployed automatically to **Cloud Run**, which handles:
   - Load balancing  
   - Auto-scaling  
   - Traffic management  
8. **Notifications** – Jenkins sends success/failure notifications after each build.

---

## 🧩 Infrastructure (GCP)

- **Compute Engine (VMs)** – Hosts Jenkins, SonarQube, and Nexus servers.  
- **Artifact Registry** – Stores versioned Docker images.  
- **Cloud Run** – Runs the deployed web app container with full scalability.  

---

## 🐳 Deployment Details

- The Docker image is built and tagged using the commit hash for versioning.  
- Jenkins authenticates with GCP using a service account key.  
- The deployment command (from Jenkins pipeline):

```bash
gcloud run deploy vprofile-app \
  --image us-central1-docker.pkg.dev/PROJECT_ID/vprofileappimg/vprofile-app:latest \
  --region us-central1 \
  --platform managed \
  --allow-unauthenticated
```

---

## 📂 Repository Structure

```
vprofile-project/
│
├── Jenkinsfile             # CI/CD pipeline definition
├── Dockerfile              # Docker image build instructions
├── scripts/                # Helper scripts for Jenkins setup
├── src/                    # Source code for the web app
├── sonar-project.properties # SonarQube configuration
└── README.md               # You’re here!
```

---

## 🧠 Key Learnings

- How to integrate Jenkins with SonarQube and Nexus for full CI/CD automation  
- How to containerize and deploy apps using Docker and GCP Cloud Run  
- Using Artifact Registry for secure image storage  
- Managing Jenkins pipelines with environment variables and credentials  

---

## 👨‍💻 Author

**Ahmed Mohamed Saad Elbardisy**  
DevOps & Cloud Enthusiast | AWS Certified Solutions Architect  
📧 [ahmedelbardicy18@gmail.com](mailto:ahmedelbardicy18@gmail.com)  
🌐 [Portfolio](https://bardicy23.github.io)

---

## 🏁 License

This project is for educational and demonstration purposes only.

