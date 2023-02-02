pipeline {
    agent any
    //{
    //     docker {
    //         image 'faelsouz/react-todo-list-app:1.0'
    //         args '-p 3000:3000'
    //     }
    // }
    stages {
        
        stage('Checkout do codigo') {
            steps {
                git url: "https://github.com/faelsou/todo-list-reactjs.git", branch: 'main'
                echo 'Fazendo checkout no repositorio'
            }
        }
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
        stage('Construção da imagem docker') {
            steps {
                script{
                    sh 'docker build -f react-todo-list-app:1.0 .' 
                    echo 'Construindo imagem docker'
                }
                
            }
        }
        stage('Docker Push') {
            steps {
                script{
                    withDockerRegistry([credentialsId: "dockerhub", url: "https://hub.docker.com/"]) {
                        sh 'docker push react-todo-list-app:1.0'
                    }
                }
            }
        }
    }
}