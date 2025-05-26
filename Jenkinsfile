pipeline{
    agent {
        label "java"
    }
    tools{
        jdk "java-8"
    }
    environment{
        XYZ='ITI ITI ITI'
    }
    parameters {
        string defaultValue: '${BUILD_NUMBER}', description: 'Enter the version of docker image', name: 'VERSION'
    }

    stages{
        stage("build Docker image"){
            steps{
                sh "docker build -t gharam/java-iti:v${VERSION} ."
            }
        }
    stages{
        stage("test Docker image"){
            steps{
                sh "docker test -t gharam/java-iti:v${VERSION} ."
            }
        }   
        stage("Push Docker image"){
            steps{
                sh "docker push gharam/java-iti:v${VERSION}"
            }
        }
    }
}
}