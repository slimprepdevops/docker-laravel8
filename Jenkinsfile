pipeline {
agent any 
stages {
    stage ('Permissions') {
        steps {
                sh 'sudo usermod -aG docker ${USER}'
                sh 'newgrp docker'
                sh 'sudo docker run hello-world'
        }
    }
        stage ('Publish') {
            steps {
                script {
                    withCredentials([string(credentialsId: 'dockerhubpwd', variable: 'dockerhubpwd')]) {
                    sh ' sudo docker login -u delalixx -p $dockerhubpwd'
                    }
                    sh 'sudo docker tag laravelchallenge:latest localhost:3000/laravelchallenge:latest'
                    sh 'sudo docker push laravelchallenget:3000/laravelchallenge:latest'
                }
            }
        }
    }
}
    
