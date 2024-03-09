pipeline {
    environment {
        dockerimagename = "aymenzarour/nginx-docker"
        dockerImage = ""
    }

    agent any

    stages {
        stage('Checkout Source') {
    steps {
        script {
            
            checkout([
                $class: 'GitSCM', 
                branches: [[name: 'main']],  
                doGenerateSubmoduleConfigurations: false, 
                userRemoteConfigs: [[
                    credentialsId: 'github-tockens', 
                    url: 'https://github.com/aymenzarour/nginx-deployment-using-jenkins.git'
                ]]
            ])
        }
    }
}

        stage('Build image') {
            steps{
                script {
                    dockerImage = docker.build dockerimagename
                }
            }
        }

        stage('Pushing Image') {
            environment {
                registryCredential = 'dockerhublogin'
            }
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', registryCredential) {
                        dockerImage.push("latest")
                    }
                }
            }
        }

        stage('Deploying App to Kubernetes') {
            
            steps {
                script {
                    sh 'kubectl apply -f  deploymentservice.yaml'
                }
            }
        }
    }
}
