pipeline {
    agent any

    stages {

        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/Nxzvi/cicd-using-jenkins.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t portfolio .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker stop portfolio-container || true
                docker rm portfolio-container || true
                docker run -d -p 80:80 --name portfolio-container portfolio
                '''
            }
        }

    }
}
