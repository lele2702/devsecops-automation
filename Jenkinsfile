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
                sh 'javac HelloWorld.java'
            }
        }

        stage('Run') {
            steps {
                // Esegui il file compilato HelloWorld.class
                sh 'java HelloWorld'
            }
        }
    }
}
