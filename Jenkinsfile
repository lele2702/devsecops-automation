pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                bat 'javac HelloWorld.java' // Compila il codice Java
            }
        }
        stage('Test') {
            steps {
                bat 'java HelloWorld' // Esegue il codice Java
            }
        }
        stage('Docker Build') {
            steps {
                script {
                    // Crea l'immagine Docker
                    docker.build("my-hello-world:${env.BUILD_ID}")
                }
            }
        }
        stage('Docker Publish') {
            steps {
                script {
                    // Pubblica l'immagine Docker su un registro Docker
                    docker.withRegistry('https://registry.example.com', 'docker-credentials') {
                        dockerImage.push()
                    }
                }
            }
        }
    }

    post {
        always {
            // Rimuovi l'immagine Docker locale dopo la build
            sh 'docker rmi my-hello-world:${env.BUILD_ID}'
        }
    }
}
