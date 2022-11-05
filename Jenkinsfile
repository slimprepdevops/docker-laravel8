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
                    withCredentials([string(credentialsId: 'dockerhubpwd', variable: 'dockerhubpwd'), string(credentialsId: 'dockerusername', variable: 'dockerusername')]) {
                    sh ' sudo docker login -u $dockerusername -p $dockerhubpwd'
                    }
                    sh 'sudo docker tag laravelchallenge delalixx/laravelchallenge'
                    sh 'sudo docker push delalixx/laravelchallenge'
                }
            }
        }
    }
}
    
