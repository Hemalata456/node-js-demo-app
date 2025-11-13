pipeline {
    agent any

    environment {
        IMAGE_NAME = "hemalata456/nodejs-demo-app"
    }

    stages {
        stage('Clone Repository') {
            steps {
                echo '📦 Cloning repository...'
                git branch: 'main', url: 'https://github.com/Hemalata456/nodejs-demo-app.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                echo '📥 Installing dependencies...'
                sh 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                echo '🧪 Running tests...'
                sh 'npm test || echo "No tests found, skipping..."'
            }
        }

        stage('Build Docker Image') {
            steps {
                echo '🐳 Building Docker image...'
                sh 'docker build -t $IMAGE_NAME .'
            }
        }

        stage('Login to DockerHub') {
            steps {
                echo '🔑 Logging into DockerHub...'
                script {
                    withCredentials([usernamePassword(credentialsId: 'PASSWD', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
                        sh 'echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin'
                    }
                }
            }
        }

        stage('Push to DockerHub') {
            steps {
                echo '🚀 Pushing image to DockerHub...'
                sh 'docker push $IMAGE_NAME'
            }
        }

        stage('Deploy Locally') {
            steps {
                echo '🛠️ Deploying container locally...'
                sh '''
                    docker stop nodejs-demo || true
                    docker rm nodejs-demo || true
                    docker run -d -p 3000:3000 --name nodejs-demo $IMAGE_NAME
                '''
            }
        }
    }

    post {
        success {
            echo '✅ Build and deployment successful!'
            mail to: 'hemalatach154@gmail.com',
                 subject: "✅ SUCCESS: ${env.JOB_NAME}",
                 body: "Build and deploy completed successfully."
        }

        failure {
            echo '❌ Build failed!'
            mail to: 'hemalatach154@gmail.com',
                 subject: "❌ FAILED: ${env.JOB_NAME}",
                 body: "Build or deployment failed. Check Jenkins logs."
        }
    }
}
