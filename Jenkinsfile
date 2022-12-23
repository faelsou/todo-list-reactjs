pipeline{
    agent{
        label "any"
    }
    stages{
        stage ("Checkout do codigo") {
            steps{
                url: 'https://github.com/faelsou/todo-list-reactjs.git',
                branch: 'main'
                echo "Fazendo checkout no repositorio"
            }

            stage ('Construção da imagem docker') {
                steps {
                    script {
                        dockerapp = docker.build("faelsouz/todolist:${env.BUILD_ID}", 
                                                '-f ./dockerfile ./')
                    }
                }
                
            }


            post{
                always{
                    echo "========always========"
                }
                success{
                    echo "========A executed successfully========"
                }
                failure{
                    echo "========A execution failed========"
                }
            }
        }
    }
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}