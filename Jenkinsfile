pipeline {
    agent any

    // Define environment variables
    environment {
        TESTING_ENVIRONMENT = "Test"
        PRODUCTION_ENVIRONMENT = "Saksham Jhamb"
    }

    stages {
        stage('Build') {
            steps {
                script {
                    echo "Using Maven for automated builds"
                    echo "Using a build automation tool to compile and package the code"
                }
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                script {
                    echo "Using JUnit for automated unit tests"
                    echo "Running unit tests"
                    echo "Using TestNG for integration tests"  
                    echo "Running integration tests"
                }
            }
            post {
                success {
                    mail(
                        to: "jhamb.saksham2408@gmail.com",
                        subject: "Test Stage - Successful",
                        body: "All the tests passed successfully :) "
                    )
                }
                failure {
                    mail(
                        to: "jhamb.saksham2408@gmail.com",
                        subject: "Test Stage - Failed",
                        body: "TEST FAILED!!!"
                    )
                }
            }
        }

        stage('Code Analysis') {
            steps {
                script {
                    echo "Using SonarQube for code quality checks"
                    echo "Checking the quality of the code"
                }
            }
        }

        stage('Security Scan') {
            steps {
                script {
                    echo "Using a security scanning tool"
                    echo "Performing security scan on the application"
                }
            }
            post {
                always {
                    mail(
                        to: "jhamb.saksham2408@gmail.com",
                        subject: "Security Scan Stage - ${currentBuild.currentResult}",
                        body: "The Security Scan stage has completed with status: ${currentBuild.currentResult}.",
                        attachLog: true
                    )
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                script {
                    echo "Using AWS CodeDeploy for deployment"
                    echo "Deploying the application to the testing environment: ${env.TESTING_ENVIRONMENT}"
                }
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                script {
                    echo "Waiting for manual approval..."
                    sleep(time: 10, unit: 'SECONDS')  
                }
            }
        }

        stage('Deploy to Production') {
            steps {
                script {
                    echo "Using Kubernetes for production deployment"
                    echo "Deploying the code to the production environment: ${env.PRODUCTION_ENVIRONMENT}"
                }
            }
        }
    }
}
