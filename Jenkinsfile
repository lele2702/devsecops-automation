pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Esegui il checkout della repository
                checkout scm
            }
        }

        stage('Compile') {
            steps {
                // Compila il file HelloWorld.java
                bat 'javac src/HelloWorld.java'
            }
        }

        stage('Docker Build') {
            steps {
                bat 'docker build -t .' // Crea l'immagine Docker
            }
        }
    }
}
