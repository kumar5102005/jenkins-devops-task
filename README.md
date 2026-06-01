# Jenkins DevOps Task — CI/CD Pipeline with Docker & Node.js

A complete CI/CD pipeline built with **Jenkins**, **Docker**, and **Node.js**, automatically cloning a GitHub repository, installing dependencies, building a Docker image, and deploying a running container — all from a single Jenkinsfile.

---

## 🚀 Pipeline Overview

| Stage | Description | Status |
|---|---|---|
| Checkout SCM | Jenkins auto-checks out the repo from GitHub | ✅ |
| Clone Repository | Clones the GitHub repo into the workspace | ✅ |
| Install Dependencies | Runs `npm install` to install Node.js packages | ✅ |
| Build Docker Image | Builds the Docker image tagged `jenkins-devops-app` | ✅ |
| Run Container | Runs the Docker container on port `3000` | ✅ |

---

## 🛠️ Tech Stack

- **Jenkins** 2.555.2
- **Git** 2.54.0 (Windows)
- **Node.js** / npm
- **Docker** (Docker Desktop for Windows)
- **GitHub** — Source Code Repository

---

## 📁 Project Structure

```
jenkins-devops-task/
├── Jenkinsfile        # Pipeline definition
├── Dockerfile         # Docker image configuration
├── package.json       # Node.js dependencies
├── index.js           # Main application file
└── README.md
```

---

## 📄 Jenkinsfile

```groovy
pipeline {
    agent any

    stages {

        stage('Clone Repository') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/kumar5102005/jenkins-devops-task.git',
                    credentialsId: '<your-credential-id>'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'npm install'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t jenkins-devops-app .'
            }
        }

        stage('Run Container') {
            steps {
                bat 'docker run -d -p 3000:3000 jenkins-devops-app'
            }
        }
    }
}
```
<img width="1366" height="768" alt="Screenshot (375)" src="https://github.com/user-attachments/assets/4beaf014-42fc-4e2b-b464-fd0dd68d63c8" />
<img width="1366" height="768" alt="Screenshot (376)" src="https://github.com/user-attachments/assets/5e9a3d10-7a15-4c08-b841-0c01812bca8b" />
<img width="1366" height="768" alt="Screenshot (377)" src="https://github.com/user-attachments/assets/735dd2df-973d-4d1a-b4d3-d4fd511cf9e7" />
---

## ⚙️ Prerequisites

Before running this pipeline, ensure the following are installed on the Jenkins machine:

- [Git for Windows](https://git-scm.com/download/win)
- [Node.js & npm](https://nodejs.org)
- [Docker Desktop](https://www.docker.com/products/docker-desktop)
- Jenkins with the following plugins:
  - Git Plugin
  - Pipeline Plugin
  - Docker Plugin

---

## 🔧 Jenkins Setup

1. **Install Git** and set the path in Jenkins:
   - Go to **Manage Jenkins → Global Tool Configuration → Git**
   - Set path to `C:\Program Files\Git\bin\git.exe`

2. **Add GitHub Credentials** (Personal Access Token):
   - Go to **Manage Jenkins → Credentials → Global → Add Credentials**
   - Kind: `Username with password`
   - Username: your GitHub username
   - Password: your GitHub Personal Access Token (PAT)

3. **Create a Pipeline Job**:
   - New Item → Pipeline
   - Under **Pipeline**, select `Pipeline script from SCM`
   - SCM: Git
   - Repository URL: `https://github.com/kumar5102005/jenkins-devops-task.git`
   - Branch: `*/main`
   - Script Path: `Jenkinsfile`

---

## ✅ Build Result

**Build #4** — `Jun 1, 2026, 7:15:44 PM`

- ⏱️ Total duration: **5 min 42 sec**
- 📦 All 5 stages passed successfully
- 🐳 Docker container running on **port 3000**
- 🌐 App accessible at: `http://localhost:3000`

### Application Output

```
Jenkins CI/CD Pipeline Working!
```

---

## 🐳 Docker Commands (Manual)

```bash
# Build the image
docker build -t jenkins-devops-app .

# Run the container
docker run -d -p 3000:3000 jenkins-devops-app

# Check running containers
docker ps

# Stop the container
docker stop <container-id>
```

---

## 🔗 Repository

**GitHub:** [https://github.com/kumar5102005/jenkins-devops-task](https://github.com/kumar5102005/jenkins-devops-task)

---

## 👤 Author

**Phani Kumar Vangali**


