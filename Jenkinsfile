pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Obtém o código-fonte do repositório
                checkout scm
            }
        }

        stage('Build') {
            steps {

                // Compila e constrói o projeto Maven
                script {
                    def mvnHome = tool 'Maven'
                    sh "chmod +x ${mvnHome}/bin/mvn"
                    sh "${mvnHome}/bin/mvn clean install"
                }
            }
        }

        stage('Test') {
            steps {
                // Executa os testes
                script {
                    def mvnHome = tool 'Maven'
                    sh "${mvnHome}/bin/mvn test"
                }
            }
        }

        stage('Deploy') {
            steps {
                // Adicione etapas de implantação aqui, se necessário
                script {
                    def mvnHome = tool 'Maven'
                    sh "${mvnHome}/bin/mvn deploy"
                }
            }
        }
    }
}
