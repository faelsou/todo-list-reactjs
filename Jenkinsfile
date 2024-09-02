pipeline {
    agent any

    environment {
        NODE_ENV = 'production'
        DEPLOY_DIR = '/var/www/todo-list-react'
        DOCKER_IMAGE = "minikube-registry.local/faelsou/todo-list-web:1.1:${env.BUILD_ID}"
        DOCKER_REGISTRY = "minikube-registry.local"
    }

    tools {
        nodejs 'NodeJS 18' // Nome da instalação configurada em "Gerenciar Jenkins"
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/faelsou/todo-list-reactjs.git'
            }
        }
        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }
        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }
    }
    
}
