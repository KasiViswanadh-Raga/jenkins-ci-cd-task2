🚀 DevOps Internship Task 2 – CI/CD Pipeline using Jenkins, Docker & Node.js

📌 Objective:

Set up a Continuous Integration and Continuous Deployment (CI/CD) pipeline using Jenkins for a Node.js application, which builds a Docker image and runs the container.


---

📁 Project Structure:

.
├── Jenkinsfile
├── Dockerfile
├── index.js
├── package.json


---

🛠 Tools Used:

Jenkins

GitHub

Docker

Node.js



---

⚙ Jenkins Pipeline Steps:

1. Clone Repository from GitHub


2. Build Docker Image


3. Run Docker Container


4. Expose App on Port 8080




---

📄 Jenkinsfile:

pipeline {
    agent any

    stages {
        stage('Clone Code') {
            steps {
                git 'https://github.com/KasiViswanadh-Raga/jenkins-ci-cd-task2.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build('ragakasiviswanadh/viswa-nodejs-app')
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    sh 'docker run -d -p 8080:8080 ragakasiviswanadh/viswa-nodejs-app'
                }
            }
        }
    }
}


---

🐳 Dockerfile:

FROM node:18

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .

EXPOSE 8080
CMD ["npm", "start"]


---

🌐 Access App:

After successful pipeline execution, open your browser and visit:

http://localhost:8080


---

🧪 Test:

You should see the output:

Hello from Node.js app running in Docker!


---

✅ Result:

A fully automated Jenkins CI/CD pipeline that:

Pulls the latest Node.js app code from GitHub

Builds a Docker image

Runs the app in a container

Exposes it on your local system at port 8080
