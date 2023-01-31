pipeline {
    agent any
    stages {
        stage("Checkout do codigo") {
            steps {
                git url: "https://github.com/faelsou/todo-list-reactjs.git",
                branch: 'main'
                echo "Fazendo checkout no repositorio"
                }
            }
            stage('Construção da imagem docker') {
                steps {
                    script {
                    dockerapp = docker.build("faelsouz/react-todo-list-app:1.0:${env.BUILD_ID}",
                                            '-f ./dockerfile ./')
                    echo "Construindo imagem docker"
                    }
                }
            }
        stage('Docker Push') {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub')
                    dockerapp.push('latest')
                    echo "Docker push da imagem docker"
                }
            }
        }
    }
}