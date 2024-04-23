pipeline {
    agent any
    environment {
        STAGING_ENVIRONMENT = "AWS EC2 instance"
    }
    stages {
        stage('Build') {
            steps {
                echo "This code is built by an automation tool - Maven"
                // Append to the log file (e.g., build.log) using '>>'
                bat 'echo Build details >> build.log'
            }
        }
        stage('Unit Test') {
            steps {
                echo "Unit test running ..."
            }
            post {
                success {
                    script {
                        def mailSubject = 'Unit Test Status - Success'
                        def mailBody = 'Unit test has been run by using test automation tool - Katalon'
                        def mailTo = 'art.random.email@gmail.com'
                        def logFile = 'build.log'

                        // Send email using the mail step
                        emailext body: "${mailBody}\n\nBuild log:\n${logFile}",
                            subject: mailSubject,
                            to: mailTo,
                            attachmentsPattern: "${logFile}",
                            mimeType: 'text/plain'
                    }
                }
                failure {
                    script {
                        def mailSubject = 'Unit Test Status - Failure'
                        def mailBody = 'Unit test has been run by using test automation tool - Katalon'
                        def mailTo = 'art.random.email@gmail.com'
                        def logFile = 'build.log'

                        // Send email using the mail step
                        emailext body: "${mailBody}\n\nBuild log:\n${logFile}",
                            subject: mailSubject,
                            to: mailTo,
                            attachmentsPattern: "${logFile}",
                            mimeType: 'text/plain'
                    }
                }
            }
        }
    }
}
