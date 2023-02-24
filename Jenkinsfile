pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                checkout([
                    $class: 'GitSCM',
                    branches: [[name: '*/main']],
                    userRemoteConfigs: [[
                        url: 'https://github.com/95remon/Simple-App-CI-CD-ITI.git',
                        credentialsId: 'GitHub'
                    ]]
                ])
            }
        }
        
        stage('Build') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'DockerHub', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                    sh """
                    ls
                    docker login -u ${USERNAME} -p ${PASSWORD}
                    docker build . -t 95remon/gcp-simple-app:v1.0
                    docker push 95remon/gcp-simple-app:v1.0
                    """
                } 
        }
        
        // Insert additional stages here
    }
}