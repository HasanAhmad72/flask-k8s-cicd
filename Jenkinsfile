pipeline {
   agent any

   stages {

       stage('Build Docker Image') {
           steps {
               bat 'docker build -t flask-cicd-app:latest .'
           }
       }

       stage('Load Image to Minikube') {
           steps {
               bat 'set "MINIKUBE_HOME=C:\\Users\\hasan" && minikube -p minikube image load flask-cicd-app:latest'
           }
       }

       stage('Deploy to Kubernetes') {
           steps {
               bat 'kubectl apply -f deployment.yaml'
               bat 'kubectl apply -f service.yaml'
           }
       }
   }
}


