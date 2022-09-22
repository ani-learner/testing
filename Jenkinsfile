pipeline {
    agent any


    environment {
        registry = "public.ecr.aws/z5v0g9o1/devops-project"
    }
    
    stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/ani-learner/testing']]])
            }
        }
        
        stage('Build') {
            steps {
                script {
                    docker.build registry
                }
            }
        }
        
        stage('Push to ECR') {
            steps {
                sh "aws ecr-public get-login-password --region us-east-1 | docker login --username AWS --password-stdin public.ecr.aws/z5v0g9o1"
                sh "docker push public.ecr.aws/z5v0g9o1/devops-project:latest"
            }
        }
        stage('Deploy to EKS') {
            steps {
               withKubeConfig(caCertificate: '', clusterName: '', contextName: '', credentialsId: 'k8s', namespace: '', serverUrl: '') {
                   sh "kubectl apply -f jenkins-deploy.yaml"
} 
            }
        }
    }
}

                

