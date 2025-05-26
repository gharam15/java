pipeline{
    agent {
        label "java"
    }
    tools{
        jdk "java-8"
    }
    environment{
         JAVA_HOME = '/usr/lib/jvm/java-8-openjdk-amd64'
        PATH = "${JAVA_HOME}/bin:${env.PATH}"
    }
    parameters {
        string defaultValue: '${BUILD_NUMBER}', description: 'Enter the version of docker image', name: 'VERSION'
    }

    stages{
        stage("build java app"){
            steps{
                sh "mvn clean package install"
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
