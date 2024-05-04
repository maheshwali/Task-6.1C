pipeline {
    agent any
    environment {
        DIRECTORY_PATH = "/path/to/code/directory"
        TESTING_ENVIRONMENT = "TestingEnvironment"
        PRODUCTION_ENVIRONMENT = "YourNameProduction"
    }
    stages {
        stage('Build') {
            steps {
                script {
                    echo "Fetching the source code from the directory path specified by the environment variable: ${env.DIRECTORY_PATH}"
                    echo "Compiling the code and generating any necessary artifacts"
                }
            }
        }
        stage('Unit and Integration Test') {
            steps {
                script {
                    echo "Running unit tests..."
                    echo "Running integration tests..."
                }
            }
        }
        stage('Code Analysis') {
            steps {
                script {
                    echo "Checking the quality of the code..."
                }
            }
        }
        stage('Security Scan') {
            steps {
                script {
                    echo "Deploying the application to a testing environment specified by the environment variable: ${env.TESTING_ENVIRONMENT}"
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                script {
                    echo "Waiting for approval..."
                    sleep time: 10, unit: 'SECONDS'
                }
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                script {
                    echo "Deploying the code to the production environment (${env.PRODUCTION_ENVIRONMENT})..."
                }
            }
        }
        stage('Deploy to Production') {
            steps {
                script {
                    echo "Deploying the code to the production environment (${env.PRODUCTION_ENVIRONMENT})..."
                }
            }
        }
    }
    post {
        success {
            emailext body: "Build successful",
                subject: "Pipeline Success",
                to: "wali.walimahesh16@gmail.com"
            echo 'Pipeline execution successful!'
        }
        failure {
            emailext body: "Build failed",
                subject: "Pipeline Failure",
                to: "wali.walimahesh16@gmail.com"
            echo 'Pipeline execution failed!'
        }
    }
}
