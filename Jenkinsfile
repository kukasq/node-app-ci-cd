pipeline {
    agent any
    
    stages {
        stage('Клонирование репозитория') {
            steps {
                git 'https://github.com/your-repository/sample-node-app.git'
            }
        }
        
        stage('Установка зависимостей') {
            steps {
                sh 'npm install'
            }
        }
        
        stage('Запуск тестов') {
            steps {
                sh 'npm test'
            }
        }
        
        stage('Сборка Docker-образа') {
            steps {
                sh 'docker build -t sample-node-app .'
            }
        }
        
        stage('Развертывание') {
            steps {
                sh '''
                    docker stop node-app || true
                    docker rm node-app || true
                    docker run -d --name node-app -p 3000:3000 sample-node-app
                '''
            }
        }
    }
}
