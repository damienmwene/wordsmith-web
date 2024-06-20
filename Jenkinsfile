pipeline {
    agent any

    tools{
        maven 'maven_3_9_7'
    }

    stages{
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