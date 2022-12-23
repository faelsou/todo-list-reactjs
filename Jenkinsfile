pipeline{
    agent any
    stages{
        stage("Checkout do codigo") {
            steps{
                git url: "https://github.com/faelsou/todo-list-reactjs.git",
                branch: 'main'
                echo "Fazendo checkout no repositorio"
            }
        }
        stage('Construção da imagem docker') {
            steps {
                script {
                    dockerapp = docker.build("faelsouz/react-todo-app:${env.BUILD_ID}", 
                                            '-f ./dockerfile ./')
                    }
                }
                
            }
        stage('Docker Push') {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com','dockerhub')
                    dockerapp.push('latest')
                
                }
            }
        }
    }
}




