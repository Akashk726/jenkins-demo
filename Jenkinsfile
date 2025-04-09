pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/yourusername/jenkins-demo.git'
            }
        }
        
        stage('Build') {
            steps {
                script {
                    docker.build("jenkins-demo:${env.BUILD_NUMBER}")
                }
            }
        }
        
        stage('Test') {
            steps {
                sh "docker run jenkins-demo:${env.BUILD_NUMBER} npm test"
            }
        }
        
        stage('Deploy') {
            steps {
                sh "docker stop jenkins-demo || true"
                sh "docker rm jenkins-demo || true"
                sh "docker run -d --name jenkins-demo -p 8080:8080 jenkins-demo:${env.BUILD_NUMBER}"
            }
        }
    }
    
    post {
        always {
            sh "docker rmi jenkins-demo:${env.BUILD_NUMBER} || true"
        }
    }
}
