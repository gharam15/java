@Library('libx') _
pipeline {
    agent {
        label 'java'
    }
    stages {
        stage('Build') {
            steps {
                buildJavaApp() 
            }
        }
    }
}
