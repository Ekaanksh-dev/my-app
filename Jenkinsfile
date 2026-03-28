pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/Ekaanksh-dev/my-app.git'
            }
        }

        stage('Build') {
            steps {
                sh 'docker compose build'
            }
        }

        stage('Deploy') {
            steps {
                sh 'docker compose up -d'
            }
        }
    }
}
