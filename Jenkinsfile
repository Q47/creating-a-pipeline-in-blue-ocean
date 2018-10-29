pipeline {
  agent {
    docker {
      image 'node:6-alpine'
    }

  }
  stages {
    stage('Build') {
      steps {
        sh 'npm install'
      }
    }
    stage('Test') {
      environment {
        CI = 'true'
      }
      steps {
        sh './jenkins/scripts/test.sh'
      }
    }
    stage('Deliver') {
      steps {
        sh './jenkins/scripts/deliver.sh'
        input 'Click "Proceed" to continue'
        sh './jenkins/scripts/kill.sh'
      }
    }
  }
}