pipeline {
    agent any

    stages {

        stage('Clone Repository') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/kumar5102005/jenkins-devops-task.git',
                    credentialsId: '62800e34-b0ae-4186-8d24-6c5009ccc8d4'
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