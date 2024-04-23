pipeline {
    agent any
    environment {
        STAGING_ENVIRONMENT = "AWS EC2 instance"
    }
    stages {
        stage('Build') {
            steps {
                echo "This code is built by an automation tool - Maven"
                // Generate a log file (e.g., build.log)
                sh 'echo "Build details" > build.log'
            }
        }
        stage('Unit Test') {
            steps {
                echo "Unit test running ..."
            }
            post {
                success {
                    // Send email using the mail step
                    mail to: 'art.random.email@gmail.com',
                         subject: 'Unit Test Status - Success',
                         body: 'Unit test has been run by using test automation tool - Katalon',
                         from: 'art.random.email@gmail.com', // Set a valid sender address
                         attachmentsPattern: 'build.log' // Attach the log file
                }
                failure {
                    // Similar configuration for failure case
                }
            }
        }
    }
}
