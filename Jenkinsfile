@Library('libx') _

pipeline {
    agent {
        label "java"
    }
    
    environment {
        IMAGE_NAME = "gharam/java-iti:${BUILD_NUMBER}"
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
                    
                    sh "docker build -t ${env.IMAGE_NAME} ."
                }
            }
        }

    }
}
