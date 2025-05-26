@Library('libx') _

pipeline {
    agent any

    environment {
        IMAGE_NAME = 'haneentharwat/java-task1'
    }

    stages {
        stage('Build Java') {
            steps {
                buildJavaApp()
            }
        }

        stage('Build Docker Image') {
            steps {
                sh "docker build -t ${imageName} ."
            }
        }

        stage('Push Docker Image') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub-cred', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
                    pushDockerImage(env.IMAGE_NAME)
                }
            }
        }
    }
}