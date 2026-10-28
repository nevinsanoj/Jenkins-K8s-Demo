pipeline {
    agent any

    environment {
        KUBECTL = 'C:/Users/nevin/AppData/Local/Programs/DockerDesktop/resources/bin/kubectl.exe'
        KUBECONFIG = 'C:/Users/nevin/.kube/config'
    }

    stages {

        stage('Clone Repository') {
            steps {
                checkout scm
            }
        }

        stage('Verify Kubernetes') {
            steps {
                bat '"%KUBECTL%" version --client'
                bat '"%KUBECTL%" get nodes'
            }
        }

        stage('Deploy Kubernetes Application') {
            steps {
                bat '"%KUBECTL%" apply -f deployment.yaml'
            }
        }

        stage('Verify Deployment') {
            steps {
                bat '"%KUBECTL%" rollout status deployment/online-book-store'
                bat '"%KUBECTL%" get deployment'
                bat '"%KUBECTL%" get pods'
            }
        }
    }
}
