pipeline{
    agent {
        label "java"
    }
    tools{
        jdk "java-8"
    }
     environment{
        DOCKER_USER = credentials('dockerhub-user')
        DOCKER_PASS = credentials('dockerhub-password')
    }

    parameters {
        string defaultValue: '${BUILD_NUMBER}', description: 'Enter the version of docker image', name: 'VERSION'
        choice choices: ['True', 'False'], description: 'skip test', name: 'Test'
    }

    stages{
        stage("build java app"){
            steps{
                sh "mvn clean package install -Dmaven.test.skip=${Test}"
            }
        }
         
        stage("build java app image"){
            steps{
                sh "docker login -u ${DOCKER_USER} -p ${DOCKER_PASS} "
                sh "docker build -t gharam/java-iti:v${VERSION} ."
            }
        }
    }
      post{
        always{
            sh "echo 'Clean the Workspace'"
            cleanWs()
        }
        failure {
            sh "echo 'failed'"
        }
    }
}
