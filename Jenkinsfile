pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'master', url: 'https://github.com/vitrubnikova/calculator-test-for-pvs.git'
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

    post post {
        success {
            emailext (
                subject: 'SUCCESS: Job ${env.JOB_NAME}',
                body: '''
                    Сборка успешно завершена!
                    Job: ${env.JOB_NAME}
                    Build: ${env.BUILD_NUMBER}
                    Подробности: ${env.BUILD_URL}
                ''',
                to: 'vitrubnikova@gmail.com'
            )
        }
        failure {
            emailext (
                subject: 'FAILURE: Job ${env.JOB_NAME}',
                body: '''
                    Сборка завершилась с ошибкой!
                    Job: ${env.JOB_NAME}
                    Build: ${env.BUILD_NUMBER}
                    Подробности: ${env.BUILD_URL}
                ''',
                to: 'vitrubnikova@gmail.com'
            )
        }
    }
}
