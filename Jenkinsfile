pipeline {
    agent any

    stages {

        stage('Clone Repo') {
            steps {
                git branch: 'main', url: 'https://github.com/karthi210/docker-and-jenkins.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t simple-website .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh '''
                docker stop website-container || true
                docker rm website-container || true
                '''
            }
        }

        stage('Run New Container') {
            steps {
                sh '''
                docker run -d \
                --name website-container \
                -p 80:80 \
                simple-website
                '''
            }
        }
    }
}
