pipeline {
    agent any

    stages {
        stage('CI') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'DockerHub', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                git 'https://github.com/95remon/Simple-App-CI-CD-ITI.git'
                sh """
                ls
                docker login -u ${USERNAME} -p ${PASSWORD}
                docker build . -t 95remon/gcp-simple-app:v1.0
                docker push 95remon/gcp-simple-app:v1.0
                """
                }
            }
        }
         stage('CD') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'DockerHub', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                git 'https://github.com/95remon/Simple-App-CI-CD-ITI.git'
                sh """
                docker login -u ${USERNAME} -p ${PASSWORD}
                """
                }
            }
        }
    }
}