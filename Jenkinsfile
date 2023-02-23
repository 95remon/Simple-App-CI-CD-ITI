pipeline {
  agent {
    docker {
      image 'docker:dind'
      args '-v /var/run/docker.sock:/var/run/docker.sock' 
    }
  }

  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }
    stage('CI') {
      steps {
        sh 'ls'
        sh 'docker build -t my-app .'
      }
    }
  }
}