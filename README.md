# Jenkins CI/CD Pipeline with SonarQube, Nexus, and Google Cloud Run
This project demonstrates a **complete CI/CD pipeline** using **Jenkins**, **SonarQube**, **Nexus**, and **Google Cloud Platform (GCP)** services. It automates the process of building, testing, analyzing, uploading artifacts, containerizing, and deploying a web application using best DevOps practices.
---
## 🚀 Overview
This project deploys a **simple web page**, originally part of a larger application (without its database or backend components). The main focus is on **showcasing a professional CI/CD pipeline** — from code commit to deployment on Cloud Run.
---
## 🧰 Tools and Technologies
- **Jenkins** – Continuous Integration and Delivery automation  
- **SonarQube** – Code quality and static analysis  
- **Nexus Repository** – Artifact storage (WAR/JAR files)  
- **GCP Artifact Registry** – Docker image hosting  
- **GCP Cloud Run** – Serverless container platform  
- **Docker** – Containerization for build and deployment  
- **GitHub** – Source code management and Jenkins webhook trigger  
- **Maven** – Build and dependency management tool  
---
## ⚙️ CI/CD Workflow (Accurate to Jenkinsfile)
1. **Code Push (GitHub)** – A commit to the `jenkins-cicd` branch triggers Jenkins automatically via a GitHub webhook.  
2. **Build Stage** – Jenkins runs `mvn -s settings.xml -DskipTests install`, builds the WAR package, and archives artifacts.  
3. **Test Stage** – Runs unit tests using Maven.  
4. **Checkstyle Analysis** – Performs static code style checks with `mvn -s settings.xml checkstyle:checkstyle`.  
5. **SonarQube Analysis** – Runs SonarQube scanner to analyze the code, then waits for a **Quality Gate** result — if it fails, the pipeline stops.  
6. **Upload Artifact (Nexus)** – If the code passes quality gates, Jenkins uploads the built `.war` file to **Nexus Repository** (`vprofile-release`).  
7. **Authenticate with GCP** – Jenkins uses stored credentials to log into GCP, set the project, and authenticate Docker with Artifact Registry.  
8. **Build Docker Image** – Builds a Docker image using the multi-stage Dockerfile.  
9. **Push Docker Image to Artifact Registry** – Pushes the image to **GCP Artifact Registry**.  
10. **Deploy to Cloud Run** – Deploys the container to Cloud Run (serverless, fully managed) using `gcloud run deploy`.  
---
## 🧩 Infrastructure on GCP
- **3 Compute Engine VMs** – Jenkins, SonarQube, and Nexus servers  
- **IAM Service Account** for Jenkins to access GCP  
- **Firewall Rules** to allow necessary ports (8080, 8081, 9000, etc.)  
- **Artifact Registry** for Docker images  
- **Cloud Run** for hosting the final app container  
---
## 🐳 Deployment Flow Summary
1. Developer pushes code → GitHub Webhook triggers Jenkins  
2. Jenkins builds, tests, analyzes with SonarQube  
3. Jenkins uploads artifact to Nexus  
4. Jenkins builds Docker image → pushes it to Artifact Registry  
5. Jenkins deploys container to Cloud Run  
6. Cloud Run auto-scales and hosts the live web app  
---
## 📂 Repository Structure
```
vprofile-project/
├── Jenkinsfile                 # Full CI/CD pipeline definition
├── Docker-files/               # Dockerfiles for app, db, web
├── gcloud-cli-setup/           # Scripts for VM, IAM, and firewall setup
├── StagePipeline/              # Jenkins pipeline & helper scripts
├── src/                        # Application source code
├── pom.xml                     # Maven build configuration
├── settings.xml                # Maven settings for Nexus credentials
└── README.md                   # This file
```
---
## 🧠 Key Learnings
- Building an end-to-end CI/CD pipeline with **Jenkins + SonarQube + Nexus + Cloud Run**  
- Uploading artifacts to Nexus before Dockerization  
- Secure GCP authentication in Jenkins with service account keys  
- Managing builds, tests, and quality gates efficiently  
- Automated deployments to a fully managed environment (Cloud Run)  
---
## 📸 Suggested Screenshots
If you want to make it visual, include:  
- ✅ Jenkins pipeline stages (successful run)  
- ✅ SonarQube Quality Gate dashboard  
- ✅ Nexus repository showing uploaded artifact  
- ✅ GCP Artifact Registry image page  
- ✅ Cloud Run service page (URL + “Active” status)  
---
## 👨‍💻 Author
**Ahmed Mohamed Saad Elbardisy**  
DevOps & Cloud Enthusiast | Suez Canal University  
📧 ahmedelbardicy18@gmail.com  
🔗 [GitHub](https://github.com/BARDICY23) | [LinkedIn](https://www.linkedin.com/in/ahmed-elbardisy/)  
---
## 🏁 License
This project is for educational and demonstration purposes only.
