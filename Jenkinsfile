pipeline {
    agent any
    tools {
        git.exe
    }
    stages {
        stage('Build') {
            steps {
                // Clona il repository Git
                git 'https://github.com/lele2702/devsecops-automation/blob/main/Jenkinsfile'

                // Compila il codice Java
                bat 'javac src/HelloWorld.java'
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
