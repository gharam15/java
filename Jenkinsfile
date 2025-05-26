@Library('libx') 

pipeline {
    agent {
        label "java"
    }
    stages {
        stage('Build') {
            steps {
                buildJavaApp()
            }
        }
    }
}
