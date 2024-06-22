pipeline {
    agent any

    tools{
        maven 'Apache Maven 3.6.3'
    }

    stages{
        stage('Maven Build') {
            steps{
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/damienmwene/wordsmith-web.git']])
                sh 'mvn clean install'
            }
        }

        stage('Build Docker Image') {
            steps{
                script{
                    sh 'docker build -t mwene/wordsmith-web .'
                }
            }
        }
        
        stage('Push to Dockerhub') {
            steps{
                sh 'docker push mwene/wordsmith-web'
            }
        }
    }
}