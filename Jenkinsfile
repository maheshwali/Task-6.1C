pipeline {
    agent any

    environment {
        EMAIL_RECIPIENTS = 'wali.walimahesh16@gmail.com'
    }

    stages {
        stage('Build') {
            steps {
                script {
                    echo 'Building the application'
                    echo 'Tool: Maven'
                    echo 'Command: mvn clean package'
                }
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                script {
                    echo 'Running unit and integration tests'
                    echo 'Tool: JUnit'
                    echo 'Command: mvn test'
                }
            }
        }
        stage('Code Analysis') {
            steps {
                script {
                    echo 'Running code analysis'
                    echo 'Tool: SonarQube'
                    echo 'Command: mvn sonar:sonar'
                }
            }
        }
        stage('Security Scan') {
            steps {
                script {
                    echo 'Running security scan'
                    echo 'Tool: OWASP Dependency Check'
                    echo 'Command: mvn dependency-check:check'
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                script {
                    echo 'Deploying to staging'
                    echo 'Method: Copy files to staging server'
                    echo 'Command: Not specified in this example'
                }
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                script {
                    echo 'Running integration tests on staging'
                    echo 'Method: Execute tests on staging environment'
                    echo 'Command: Not specified in this example'
                }
            }
        }
        stage('Deploy to Production') {
            steps {
                script {
                    echo 'Deploying to production'
                    echo 'Method: Copy files to production server'
                    echo 'Command: Not specified in this example'
                }
            }
        }
    }

    post {
        always {
            echo 'Cleaning up...'
        }
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }

    post {
        stage('Unit and Integration Tests') {
            success {
                emailext (
                    to: "${env.EMAIL_RECIPIENTS}",
                    subject: "Build Successful: Unit and Integration Tests",
                    body: "The Unit and Integration Tests stage completed successfully.",
                    attachLog: true
                )
            }
            failure {
                emailext (
                    to: "${env.EMAIL_RECIPIENTS}",
                    subject: "Build Failed: Unit and Integration Tests",
                    body: "The Unit and Integration Tests stage failed. Please check the logs.",
                    attachLog: true
                )
            }
        }

        stage('Security Scan') {
            success {
                emailext (
                    to: "${env.EMAIL_RECIPIENTS}",
                    subject: "Build Successful: Security Scan",
                    body: "The Security Scan stage completed successfully.",
                    attachLog: true
                )
            }
            failure {
                emailext (
                    to: "${env.EMAIL_RECIPIENTS}",
                    subject: "Build Failed: Security Scan",
                    body: "The Security Scan stage failed. Please check the logs.",
                    attachLog: true
                )
            }
        }
    }
}
