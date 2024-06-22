pipeline {
    agent any

    environment {
        SONARQUBE_SERVER = 'MySonarQubeServer'
        SONARQUBE_TOKEN = credentials('sonartoken')
    }

    tools{
        maven 'Apache Maven 3.6.3'
    }

    stages{
        stage('SonarQube Analysis') {
            steps {
                script {
                    def scannerHome = tool 'SonarQube Scanner';
                    withSonarQubeEnv('MySonarQubeServer') {
                        sh "${scannerHome}/bin/sonar-scanner \
                            -Dsonar.projectKey=my_project_key \
                            -Dsonar.sources=. \
                            -Dsonar.host.url=http://localhost:9000 \
                            -Dsonar.login=${SONARQUBE_TOKEN}"
                    }
                }
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