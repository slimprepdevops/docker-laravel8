pipeline {
agent any 
stages {
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
