pipeline {
    agent any

    environment {
        NODE_ENV = 'production'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/faelsou/todo-list-reactjs.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                script {
                    sh 'npm install'
                }
            }
        }

        stage('Lint') {
            steps {
                script {
                    sh 'npm run lint'
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    sh 'npm test'
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    sh 'npm run build'
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                   // Exemplo de deploy para o S3 da AWS
//                    sh 'aws s3 sync build/ s3://meu-bucket-s3 --delete'
                }
            }
        }
    }

    post {
        always {
            echo 'Pipeline concluída.'
        }
        success {
            echo 'Aplicação React construída com sucesso.'
        }
        failure {
            echo 'Erro na execução da pipeline.'
        }
    }
}
