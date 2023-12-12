pipeline {
    agent any
    environment {
        PROJECT = "WELCOME TO EKS"
    }
    stages {
     stage('Check The Kubernetes Access') {
        steps {
         sh 'aws eks --region us-east-2 update-kubeconfig --name k8sb21'
         sh 'kubectl get pods -A'
         sh 'kubectl get ns'
        }
      }
     stage('Deploy Voting App') {
        steps {
         sh 'ls -al'
         sh 'kubectl apply -f voting-with-ingress.yml'
         sh 'kubectl apply -f ingress.yml'
         sh 'kubectl get pods,svc,ingress'
        }         
     }
     stage('Deploy Ingress for Vote & Result') {
        steps {
         sh 'kubectl apply -f ingress.yml'
         sh 'kubectl get ingress'
        }         
     }
     stage('Validating Deployment') {
        steps {
         sh 'kubectl get pods,deployment,svc'
        }         
     }
    }
}