pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'test', url: 'https://github.com/vitrubnikova/calculator-test-for-pvs.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build("calc:${env.BUILD_ID}")
                }
            }
        }
    }

    post {
        success {
            script {
                telegramSend(message: 'Hello World')
            }
        }
        failure {
            script {
                telegramSend 'Hello World'
            }
        }
    }
}
