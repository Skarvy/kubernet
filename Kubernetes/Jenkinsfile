pipeline {
    agent any

   
    
    stages {
        stage('Checkout Code') {
            steps {
                // Clona el repositorio de GitHub en la rama main
                git branch: 'main', url: 'https://github.com/Skarvy/kubernet'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                script {
                    // Asegúrate de que kubectl esté configurado en tu máquina Jenkins o que tenga acceso al clúster
                    // Aplica los manifiestos YAML para el backend, frontend, MongoDB y Redis
                    sh 'kubectl apply -f kubernetes/backend-deployment.yaml '
                    sh 'kubectl apply -f kubernetes/backend-service.yaml'
                    
                    sh 'kubectl apply -f kubernetes/frontend-deployment.yaml'
                    sh 'kubectl apply -f kubernetes/frontend-service.yaml'

                    
                    sh 'kubectl apply -f kubernetes/mongo-deployment.yaml'
                    sh 'kubectl apply -f kubernetes/mongo-service.yaml'


                    sh "kubectl apply -f kubernetes/configmap/mongo-data.yaml"


                    
                    sh 'kubectl apply -f kubernetes/redis-deployment.yaml'
                    sh 'kubectl apply -f kubernetes/redis-service.yaml'
                }
            }
        }
    }
}
