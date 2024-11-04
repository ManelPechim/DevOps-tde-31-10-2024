pipeline {
    agent any

    stages {
        stage('Cleanup') {
            steps {
                script {
                    // Derruba containers em execução e remove imagens antigas
                    sh 'docker-compose down'
                    sh 'docker rmi -f docker-project_flask_app || true'
                    sh 'docker rmi -f docker-project_mariadb || true'
                }
            }
        }

        stage('Start Services') {
            steps {
                script {
                    // Inicia os containers com docker-compose
                    sh 'docker-compose up -d'
                    sh 'docker-compose down'
                    sh 'docker rmi -f docker-project_flask_app || true'
                    sh 'docker rmi -f docker-project_mariadb || true'

                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline executado com sucesso!'
        }
        failure {
            echo 'Pipeline falhou.'
        }
    }
}
