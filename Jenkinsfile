pipeline {
    agent any

    tools{
        maven 'Apache Maven 3.6.3'
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