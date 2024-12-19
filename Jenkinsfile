pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                // Realiza el checkout
                checkout scm
                
                // Imprime el directorio actual
                sh 'pwd'
                
                // Lista el contenido del directorio
                sh 'ls -la'
            }
        }
    }
}
