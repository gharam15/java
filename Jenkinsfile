@Library('libx')_

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
        stage("vim info"){
            steps{
                script{
                    def VM_IP =vimip()
                }
                       
            }
        }
        stage("build java app"){
            steps{
                script{
                    sayhello.infoip 'iti'
                }
                sh "mvn clean package install -Dmaven.test.skip=${Test}"          
            }
        }
        stage("build java app image"){
            steps{
                script{
                    def dockerx = new org.iti.docker()
                    dockerx.build('java',"${VERSION}")
                }
                sh "docker login -u ${DOCKER_USER} -p ${DOCKER_PASS} "
                
            }
        }
         stage("push java app image"){
            steps{
                script{
                    def dockerx = new org.iti.docker()
                    dockerx.login("${DOCKER_USER}","${DOCKER_PASS}")
                    dockerx.push("${DOCKER_USER}","${DOCKER_PASS}")
 
                }  
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
