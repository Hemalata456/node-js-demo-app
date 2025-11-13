Node.js CI/CD Pipeline using Jenkins and Docker 

📂 Dataset/Repo Dataset/Repo Name: node-demo-app 


📋 Project Overview 
This project demonstrates an automated CI/CD pipeline for a simple Node.js web application using Jenkins and Docker. Whenever code is pushed to this GitHub repository, Jenkins automatically: 

1. Pulls the latest code 
2. Installs dependencies 
3. Runs tests 
4. Builds a Docker image 
5. Pushes it to DockerHub (hemalata456/node-cicd-demo) 
6. Deploys the container locally on the Jenkins server 
7. Sends an email notification if the pipeline fails 


⚙️ Tools Used 

| Tool          | Purpose                                       |
| ------------- | --------------------------------------------- |
| **Jenkins**   | Automates the build, test, and deploy process |
| **GitHub**    | Stores and triggers the code for the pipeline |
| **Docker**    | Containerizes the Node.js app                 |
| **DockerHub** | Stores the built Docker image                 |
| **Node.js**   | Application runtime                           |


🧱 Folder Structure 

nodejs-demo-app/ 
├── app.js 
├── package.json 
├── Dockerfile 
├── Jenkinsfile 
├── README.md 
└── screenshots/ 


🔗 Repository URL 
👉 https://github.com/hemalata456/nodejs-demo-app 


🧩 Pipeline Flow (Using Jenkinsfile) 

| Stage                    | Description                                        |
| ------------------------ | -------------------------------------------------- |
| **Checkout Code**        | Pulls latest code from GitHub                      |
| **Install Dependencies** | Installs packages using `npm install`              |
| **Run Tests**            | Runs test command (`npm test`)                     |
| **Build Docker Image**   | Creates a Docker image for the app                 |
| **Push to DockerHub**    | Pushes image to DockerHub repository               |
| **Deploy Container**     | Runs the container locally on Jenkins server       |
| **Post (Failure Email)** | Sends short fail info to `hemalatach154@gmail.com` |



⚡ Jenkins Configuration Item Type: 
Pipeline Definition: 
Pipeline script from SCM Repository URL: https://github.com/hemalata456/nodejs-demo-app.git 
Script Path: Jenkinsfile 
Poll SCM: Every 1 minute (H/1 * * * *) 
Email: Configured using Email Extension Plugin Sends a short message only when the build fails 


🖥️ Deployment The app runs locally on the Jenkins server and can be accessed at: 
http://<jenkins-server-ip>:3000 


🧠 Learning Outcome 
By completing this project, I learned: 

How to set up an end-to-end CI/CD pipeline using Jenkins 
How to automate Docker image build and push process 
How to configure Poll SCM triggers and email alerts 
How to document and organize a project for submission 


👤 Author 

*Challa Hemalata* 
DevOps Intern | Cloud Enthusiast 
📧 Email: hemalatach154@gmail.com 
🔗 GitHub: @hemalata456 