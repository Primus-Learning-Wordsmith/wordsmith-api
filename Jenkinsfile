pipeline {
    agent any

    tools{
        maven 'Apache Maven 3.9.8'
    }
    
    stages{
        stage('Maven Build') {
            steps{
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Primus-Learning-Wordsmith/wordsmith-api.git']])
                sh 'mvn clean install'
            }
        }
        
        stage('Build Docker Image') {
            steps{
                script{
                    sh 'docker build -t wordsmith-api:latest .'
                }
            }
        }
        
        stage('Push to Dockerhub') {
            steps{
                sh 'docker push grace414/wordsmith-api:latest'
            }
        }
    }
}