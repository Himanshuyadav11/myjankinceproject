pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/seelimsii/Netflix-clone.git'
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
