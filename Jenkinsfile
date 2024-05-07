pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                // Checkout code from Git repository
                checkout scm
                //git url: 'https://github.com/alfatmi1993/Intern.git', credentialsId: 'f8d0256c-143b-4393-9ac5-7651d8bc82c9'
                // Build the application (replace with your build commands)
                sh 'mvn clean package'
            }
        }
        
        stage('Test') {
            steps {
                // Run automated tests (replace with your test commands)
                sh 'mvn test'
            }
        }
        
        stage('Deploy') {
            steps {
                // Package the application into a Docker container
                sh 'docker build -t intern/rich .'
                
                // Push the container to Docker Hub or a private registry
                sh 'docker push intern/rich'
                
                // Deploy the application to a test/staging environment
                // Replace this with your deployment commands (e.g., Kubernetes deployment, Docker-compose, etc.)
                sh 'kubectl apply -f sind.yaml'
            }
        }
    }
    
    post {
        success {
            // Actions to take if the pipeline succeeds
            echo 'Pipeline succeeded! Application deployed.'
        }
        failure {
            // Actions to take if the pipeline fails
            echo 'Pipeline failed! Application deployment aborted.'
        }
    }
}
