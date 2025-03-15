pipeline {
    agent any

    stages {
        // Этап 1: Клонирование репозитория
        stage('Clone Repository') {
            steps {
                git branch: 'master', url: 'https://github.com/vitrubnikova/calculator-test-for-pvs.git'
            }
        }

        // Этап 2: Сборка Docker-образа
        stage('Build Docker Image') {
            steps {
                script {
                    // Указываем имя образа
                    dockerImage = docker.build("calc:${env.BUILD_ID}")
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline выполнен успешно!'
        }
        failure {
            echo 'Pipeline завершился с ошибкой.'
        }
    }
}
