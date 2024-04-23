pipeline {
    agent any
    environment {
        STAGING_ENVIRONMENT = "AWS EC2 instance"
    }
    stages {
        stage('Build') {
            steps {
                echo "This code is built by an automation tool - Maven"
            }
        }
        stage('Unit Test') {
            steps {
                echo "Unit test running ..."
            }
            post {
                success {
                    emailext subject: "Unit Test Status - Success",
                             body: "Unit test has been run successfully using test automation tool - Katalon",
                             to: "art.random.email@gmail.com",
                             attachLog: true
                }
                failure {
                    emailext subject: "Unit Test Status - Failure",
                             body: "Unit test has failed using test automation tool - Katalon",
                             to: "art.random.email@gmail.com",
                             attachLog: true
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo "Quality of the code is being checked by code analysis tool - PMD"
                // Add code analysis steps here
            }
        }
        stage('Security Scan') {
            steps {
                echo "Scanning code for security vulnerabilities using OWASP ZAP"
                // Add security scan steps here
            }
            post {
                success {
                    emailext subject: "Security Scan Status - Success",
                             body: "Security scan on the code has been successful using OWASP ZAP",
                             to: "art.random.email@gmail.com",
                             attachLog: true
                }
                failure {
                    emailext subject: "Security Scan Status - Failure",
                             body: "Security scan on the code has failed using OWASP ZAP",
                             to: "art.random.email@gmail.com",
                             attachLog: true
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo "The application is being deployed to a staging server - ${STAGING_ENVIRONMENT}"
                // Add deployment steps to staging environment here
            }
        }
        stage('Integration Test') {
            steps {
                echo "Integration test on the ${STAGING_ENVIRONMENT} has been run by using test automation tool - Katalon"
                // Add integration test steps here
            }
        }
        stage('Deploy to Production') {
            steps {
                echo "The application is being deployed to a production server - ${STAGING_ENVIRONMENT}"
                // Add deployment steps to production environment here
            }
        }
    }
}
