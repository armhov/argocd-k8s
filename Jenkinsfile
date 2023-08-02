
pipeline {
  agent any

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
        sh "echo hello world'""
    }
  }
  post {
    always {
        cleanWs()
    }
  }
}
