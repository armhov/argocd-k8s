
pipeline {
  agent any
  environment {
    DOCKERHUB_CREDENTIALS = credentials('docker-hub-creds')
  }

//   environment {
// 		AWS = credentials('aws-jenkins-role-credentials')
// 		BRANCH          = '${env.BRANCH_NAME}'
//     SERVICE_REPO_CREDENTIALS_ID = 'git-apl1'
// 	}

  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }

    stage('Test stage') {
      steps {
        echo "Hello world"
      }
    }
    stage('Push image') {
        withDockerRegistry([ credentialsId: "dockerhubaccount", url: "" ]) {
        dockerImage.push()
      }
    }

  }
  post {
    always {
        cleanWs()
    }
  }
}



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
//     stage('Build') {
//       steps {
//         sh 'docker build -t lloydmatereke/jenkins-docker-hub .'
//       }
//     }
//     stage('Login') {
//       steps {
//         sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
//       }
//     }
//     stage('Push') {
//       steps {
//         sh 'docker push lloydmatereke/jenkins-docker-hub'
//       }
//     }
  }
  post {
    always {
      sh 'docker logout'
    }
  }
}