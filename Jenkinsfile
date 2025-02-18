pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'dev', credentialsId: 'f690bf34-dc2b-4a37-ad7d-e52d1d76c3ddA', url: 'https://github.com/jackm2030/jenkins-automation'
            }
        }
        stage('Build') {
            steps {
                sh 'echo "Construyendo el proyecto..."'
            }
        }
        stage('Test') {
            steps {
                sh 'echo "Ejecutando pruebas..."'
            }
        }
        stage('Deploy') {
            steps {
                sh 'echo "Desplegando la aplicación..."'
            }
        }
    }
}
