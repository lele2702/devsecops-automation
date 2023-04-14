pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                bat 'javac HelloWorld.java' // Compila il file Java
            }
        }
        stage('Test') {
            steps {
                bat 'java HelloWorld' // Esegue il file Java
            }
        }
        stage('Docker Build') {
            steps {
                bat 'docker build -t hello-world .' // Crea l'immagine Docker
            }
        }
        stage('Docker Push') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'docker-hub', passwordVariable: 'DOCKER_PASSWORD', usernameVariable: 'DOCKER_USERNAME')]) {
                    // Utilizza le credenziali Docker Hub
                    bat "docker login -u %DOCKER_USERNAME% -p %DOCKER_PASSWORD%" // Effettua l'accesso a Docker Hub
                }
                bat 'docker push hello-world' // Carica l'immagine Docker su Docker Hub
            }
        }
    }
}
