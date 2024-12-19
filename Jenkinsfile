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
                    
                    sh 'kubectl apply -f Kubernetes/frontend/frontend-deployment.yaml'
                    sh 'kubectl apply -f Kubernetes/frontend/frontend-service.yaml'

                    sh "kubectl apply -f Kubernetes/mongo/configmap/mongo-data.yaml"
                    
                    sh 'kubectl apply -f Kubernetes/mongo/mongo-deployment.yaml'
                    sh 'kubectl apply -f Kubernetes/mongo/mongo-service.yaml'


                  


                    
                    sh 'kubectl apply -f Kubernetes/redis/redis-deployment.yaml'
                    sh 'kubectl apply -f Kubernetes/redis/redis-service.yaml'


                    sh 'kubectl apply -f Kubernetes/backend/backend-deployment.yaml '
                    sh 'kubectl apply -f Kubernetes/backend/backend-service.yaml'
                    
                }

            }
        }
    }
}
