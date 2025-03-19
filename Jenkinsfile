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
            emailext (
                subject: 'SUCCESS: Job ${env.JOB_NAME}',
                body: 'Сборка успешно завершена!',
                to: 'vitrubnikova@gmail.com'
            )
        }
        failure {
            emailext (
                subject: 'FAILURE: Job ${env.JOB_NAME}',
                body: 'Сборка завершилась с ошибкой!',
                to: 'vitrubnikova@gmail.com'
            )
        }
    }
}
