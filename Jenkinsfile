pipeline {
  agent any

  environment {
    ACCOUNT_UNAME = "armhov"
    APP_NAME = "flask-app"
    VERSION = "${env.BUILD_ID}-${env.GIT_COMMIT}"
    IMAGE = "${NAME}:${VERSION}"
    DOCKERHUB_CREDENTIALS = credentials('docker-hub-creds')
  }
  stages {
    stage('Echo creds'){
        steps {
            sh 'echo $DOCKERHUB_CREDENTIALS_PSW'
            sh 'echo $DOCKERHUB_CREDENTIALS_USR'
        }
    }

    stage('Build and tag image') {
      steps {
        sh 'docker build -t ${ACCOUNT_UNAME}/${APP_NAME} .'
        sh 'docker tag ${ACCOUNT_UNAME}/${APP_NAME} ${ACCOUNT_UNAME}/${APP_NAME}:${VERSION}'
      }
    }

    stage('Login') {
      steps {
        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
      }
    }
    stage('Push') {
      steps {
        sh 'docker push ${ACCOUNT_UNAME}/${APP_NAME}:${VERSION}'
      }
    }


  }
  post {
    always {
      sh 'docker logout'
    }
  }
}