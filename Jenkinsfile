pipeline {
    agent any

    tools{
        maven 'maven_3_9_7'
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