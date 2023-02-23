pipeline {
    agent none
    stages {
        stage('Build') {
            agent {
                docker {
                    image 'docker:latest'
                    args '-v /var/run/docker.sock:/var/run/docker.sock'
                }
            }
            steps {
                sh 'ls'
                sh 'docker build -t myimage .'
            }
        }
        
    }
}
