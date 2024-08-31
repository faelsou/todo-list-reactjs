pipeline {
    agent any

    environment {
        NODE_ENV = 'production'
    }
        DEPLOY_DIR = '/var/www/todo-list-react'
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
    }
    
}
