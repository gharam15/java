pipeline{
    agent {
        label "java"
    }
    tools{
        jdk "java-8"
    }
    parameters {
        string defaultValue: '${BUILD_NUMBER}', description: 'Enter the version of docker image', name: 'VERSION'
        choice choices: ['true', 'false'], description: 'skip test', name: 'Test'
    }

    stages{
        stage("build java app"){
            steps{
                sh "mvn clean package install -Dmaven test.skip=${Test}"
            }
        }
         
        stage("build java app image"){
            steps{
                sh "docker build -t gharam/java-iti:v${VERSION} ."
            }
        }
    }
}
