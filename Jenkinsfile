pipeline {
    agent any 
    environment {
        DOCKERHUB_CREDENTIALS_PSW = "Owsn5g7a\$\$\$"
        DOCKERHUB_CREDENTIALS_USR = "ashraf_amad@hotmail.com"
    }
    stages { 

        stage('Build docker image') {
            steps {  
                sh 'echo  | sudo -S docker build -t ashrafamad/flaskapp:$BUILD_NUMBER .'
            }
        }
        stage('login to dockerhub') {
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | echo  | sudo -S docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('push image') {
            steps{
                sh 'echo  | sudo -S docker push ylmt/flaskapp:$BUILD_NUMBER'
            }
        }
}
post {
        always {
            sh 'echo  | sudo -S docker logout'
        }
    }
}
