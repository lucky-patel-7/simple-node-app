pipeline {
  agent {
    docker {
      image 'node:6-alpine'
      args '-v /var/run/docker.sock:/var/run/docker.sock -v C:/ProgramData/Jenkins/.jenkins/workspace/test:/app'
    }
  }
  stages {
    stage('Build') {
      steps {
        checkout scm
        sh 'npm install'
        sh 'npm run build'
      }
    }
    stage('Test') {
      steps {
        sh 'npm test'
      }
    }
    stage('Deliver') {
      steps {
        sh 'npm run deploy'
      }
    }
  }
}
