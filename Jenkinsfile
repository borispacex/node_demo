pipeline {
    agent any
    environment {
        DOCKERHUB_CREDENTIALS = credentials('docker-hub-credentials')
    }
    stages {
        stage('Clonar Repositorio') {
            steps {
                git branch: 'main', credentialsId: 'github-credentials', url: 'https://github.com/borispacex/node_demo.git'
            }
        }
        stage('Ejecutar Pruebas') {
            steps {
                sh 'npm install'
                sh 'npm test'
            }
        }
        stage('Construir Imagen de Docker') {
            steps {
                sh 'docker build -t borispacex/node_demo:latest .'
            }
        }
        stage('Enviar a Docker Hub') {
            steps {
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
                sh 'docker push borispacex/node_demo:latest'
            }
        }
    }
}