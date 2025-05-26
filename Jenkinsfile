@Library('libx') _
pipeline {
    agent { label 'java' }
    stages {
        stage('Build') {
            steps {
                buildJavaApp()
            }
        }
        stage('Docker') {
            steps {
                script {
                    def imageName = 'my-java-app:latest'
                    buildDockerImage(imageName)
                    pushDockerImage(imageName)
                }
            }
        }
    }
}
