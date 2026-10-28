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

        stage('Create Kubernetes Pod') {
            steps {
                bat '"%KUBECTL%" apply -f pod.yaml'
            }
        }

        stage('Verify Pod') {
            steps {
                bat '"%KUBECTL%" get pod jenkins-k8s-demo-pod'
            }
        }
    }
}
