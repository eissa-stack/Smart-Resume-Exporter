pipeline {
    agent any
    stages {
        stage('Clone Repo') {
            steps {
                script {
                    try {
                        sh 'git clone https://github.com/eissa-stack/Smart-Resume-Exporter.git'
                        echo 'successfully cloned repository'
                    } catch (Exception e) {
                        echo 'failed to clone repository'
                        error('Stopping pipeline')
                    }
                }
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    try {
                        dir('Smart-Resume-Exporter') {
                            sh 'docker build -t smart-resume-exporter .'
                        }
                        echo 'successfully built docker image'
                    } catch (Exception e) {
                        echo 'failed to build docker image'
                        error('Stopping pipeline')
                    }
                }
            }
        }
        stage('Run Docker Container') {
            steps {
                script {
                    try {
                        sh 'docker run -d -p 8000:8000 --name smart-resume-exporter smart-resume-exporter'
                        echo 'successfully ran docker container'
                    } catch (Exception e) {
                        echo 'failed to run docker container'
                        error('Stopping pipeline')
                    }
                }
            }
        }
    }
}
