pipeline {
    agent any
    environment {
    DOCKERHUB_CREDENTIALS = credentials('dh_cred')
    stages {
        stage('Checkout') {
            steps {
            git'https://github.com/Rabebkh/Springdocker.git'
              checkout scm
            }
    }
    stage('Build docker image') {
        steps {
          sh 'docker build -t rabebkhaled/springapp:$BUILD_ID .'
        }
   stage('login to dockerhub') {
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('push image') {
            steps{
                sh 'docker push rabebkhaled/springapp:$BUILD_ID'
            }
        }
}
post {
        always {
            sh 'docker logout'
        }
    }
}
}
}
