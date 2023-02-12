pipeline {
    agent any 
    environment {
        DOCKERHUB_CREDENTIALS_PSW = "Owsn5g7a\$\$\$"
        DOCKERHUB_CREDENTIALS_USR = "ashraf_amad@hotmail.com"
    }
    stages { 

        stage('Build docker image') {
            steps {  
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | sudo -S docker build -t ashrafamad/flaskapp:$BUILD_NUMBER .'
            }
        }
        stage('login to dockerhub') {
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | sudo docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('push image') {
            steps{
                sh 'sudo docker push ylmt/flaskapp:$BUILD_NUMBER'
            }
        }
}
post {
        always {
            sh 'sudo docker logout'
        }
    }
}
