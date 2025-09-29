pipeline {
    agent any
    stages {
        stage('Clone Repo') {
            steps {
                cleanWs()
                git url: 'https://github.com/eissa-stack/Smart-Resume-Exporter.git'
                echo 'Cloned repository successfully.'
            }
        }
        stage('Build Docker Image') {
            steps {
                dir('Smart-Resume-Exporter') {
                    sh 'docker build -t smats .'
                }
                echo 'Docker image built successfully.'
            }
        }
        stage('Run Docker Container') {
            steps {
                sh 'docker run -d -p 8000:8000 smats'
                echo 'Docker container running successfully.'
            }
        }
    }
}
