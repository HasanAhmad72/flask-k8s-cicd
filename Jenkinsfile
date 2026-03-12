pipeline {
   agent any

   stages {

     stage('Clone Code') {
    steps {
        git branch: 'main', url: 'https://github.com/HasanAhmad72/flask-k8s-cicd.git'
    }
}

       stage('Build Docker Image') {
           steps {
               bat 'docker build -t flask-cicd-app:latest .'
           }
       }

       stage('Load Image to Minikube') {
           steps {
               bat 'minikube image load flask-cicd-app:latest'
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
