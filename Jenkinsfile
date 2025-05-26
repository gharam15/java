@Library('libx') _

pipeline {
    agent {
        label "java"
    }

    stages {
        stage('Build Java') {
            steps {
                buildJavaApp()
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    echo "Building Docker image with tag: ${env.IMAGE_NAME}"
                    sh "docker build -t gharam/java-iti:${BUILD_NUMBER} ."
                }
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
