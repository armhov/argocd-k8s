pipeline {
  agent any

  environment {
    DOCKERHUB_CREDENTIALS = credentials('docker-hub-creds')
  }
  stages {
    stage('Echo creds'){
        steps {
            sh 'echo $DOCKERHUB_CREDENTIALS_PSW'
            sh 'echo $DOCKERHUB_CREDENTIALS_USR'
        }
    }
  }
  post {
    always {
      sh 'docker logout'
    }
  }
}