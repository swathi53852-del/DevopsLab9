pipeline {
    agent any
    stages {
        stage('Build Docker Image') {
            steps {
                bat 'docker build -t flaskapp .'
            }
        }
        stage('Run Dev Container') {
            steps {
                bat 'docker rm -f dev-container 2>nul || exit /b 0'
                bat 'docker run -d --name dev-container -p 5002:5000 flaskapp'
            }
        }
        stage('Run Test Container') {
            steps {
                bat 'docker rm -f test-container 2>nul || exit /b 0'
                bat 'docker run -d --name test-container -p 5003:5000 flaskapp'
            }
        }
    }
}
