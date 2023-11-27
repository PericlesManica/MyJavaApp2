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

        stage('Run Application') {
            steps {
                // Executa a aplicação Java após a construção
                script {
                    sh "java -jar target/my-java-app-1.0-SNAPSHOT.jar"
                }
            }
        }
    }
}
