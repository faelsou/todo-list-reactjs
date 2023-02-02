pipeline {
    agent any

    stages {
        stage('Checkout do codigo') {
            steps {
                git url: "https://github.com/faelsou/todo-list-reactjs.git", branch: 'main'
                echo 'Fazendo checkout no repositorio'
            }
        }
        stage('Construção da imagem docker') {
            steps {
                script{
                    sh 'docker build -f faelsouz/react-todo-list-app:1.0 .' 
                    echo 'Construindo imagem docker'
                }
                
            }
        }
        // stage('Docker Push') {
        //     steps {
        //         script{
        //             docker.withRegistry('https://registry.hub.docker.com', 'dockerhub')
        //             echo 'Deploying....'
        //         }
        //
        //     }
        // }
    }
}