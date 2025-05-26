pipeline{
    agent {
        label "java"
    }
    tools{
        jdk "java-8"
    }
    environment{
        JAVA_HOME="/home/jenkins/tools/hudson.model.JDK/java-8/openlogic-openjdk-8u442-b06-linux-x64"
    }
    parameters {
        string defaultValue: '${BUILD_NUMBER}', description: 'Enter the version of docker image', name: 'VERSION'
    }

    stages{
        stage("build java app"){
            steps{
                sh "mvn clean package install ."
            }
        }
        stage("test java app"){
            steps{
                sh "mvn test"
            }
        }   
        stage("build java app image"){
            steps{
                sh "docker build -t gharam/java-iti:v${VERSION} ."
            }
        }
    }
}
