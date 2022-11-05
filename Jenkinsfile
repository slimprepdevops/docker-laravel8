pipeline {
agent any 
stages {
    stage ('Permissions') {
        steps {
                sh 'sudo usermod -aG docker ${USER}'
                sh 'su -s ${USER}'
                sh 'docker run hello-world'
                sh 'sudo chown "$USER":"$USER" /home/"$USER"/.docker -R'
                sh 'sudo chmod g+rwx "$HOME/.docker" -R'
        }
    }
        stage ('Publish') {
            steps {
                script {
                    withCredentials([string(credentialsId: 'dockerhubpwd', variable: 'dockerhubpwd')]) {
                    sh 'docker login -u delalixx -p $dockerhubpwd'
                    }
                    sh 'docker push delalixx/larvel8:laravelchallenge'
                }
            }
        }
    }
}
    
