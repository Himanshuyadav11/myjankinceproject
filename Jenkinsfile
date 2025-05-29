pipeline {
    environment {
        AWS_ACCESS_KEY_ID     = credentials('AWS_ACCESS_KEY_ID')
        AWS_SECRET_ACCESS_KEY = credentials('AWS_SECRET_ACCESS_KEY')
    }

    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Himanshuyadav11/myjankinceproject.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build('netflix-clone')
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    docker.image('netflix-clone').run('-d -p 80:80')
                }
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished.'
        }
    }
}
