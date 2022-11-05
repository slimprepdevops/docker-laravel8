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
                    sh 'sudo docker push delalixx/larvel8:laravelchallenge'
                }
            }
        }
    }
}
    
