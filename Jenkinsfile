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
                telegramSend (
                    message: """
                        ✅ Сборка успешно завершена!
                        Job: ${env.JOB_NAME}
                        Build: ${env.BUILD_NUMBER}
                        Подробности: ${env.BUILD_URL}
                    """
                )
            }
        }
        failure {
            script {
                telegramSend (
                    message: """
                        ❌ Сборка завершилась с ошибкой!
                        Job: ${env.JOB_NAME}
                        Build: ${env.BUILD_NUMBER}
                        Подробности: ${env.BUILD_URL}
                    """
                )
            }
        }
    }
}
