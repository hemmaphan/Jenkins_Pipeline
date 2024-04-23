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
                    script {
                        def unitTestLog = readFile '**/test-results/*.xml'
                        sendEmailWithAttachment("Unit Test Status: ${currentBuild.result}", "Unit test has been run by using test automation tool - Katalon", "art.random.email@gmail.com", unitTestLog, "unit-test-log.xml")
                    }
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo "Quality of the code has been checked by code analysis tool - PMD"
            }
        }
        stage('Security Scan') {
            steps {
                echo "Scanning ..."
            }
            post {
                success {
                    script {
                        def securityScanLog = readFile '**/security-scan-results/*.txt'
                        sendEmailWithAttachment("Security Scan Status: ${currentBuild.result}", "A security scan on the code has been scanned by OWASP ZAP", "art.random.email@gmail.com", securityScanLog, "security-scan-log.txt")
                    }
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo "The application has been deployed to a staging server - AWS EC2 instance"
            }
        }
        stage('Integration Test') {
            steps {
                echo "Integration test on the $STAGING_ENVIRONMENT has been run by using test automation tool - Katalon"
            }
        }
        stage('Deploy to Production') {
            steps {
                echo "The application has been deployed to a production server - AWS EC2 instance"
            }
        }
    }
}

def sendEmailWithAttachment(String subject, String body, String to, String attachmentContent, String attachmentFileName) {
    emailext (
        subject: subject,
        body: body,
        to: to,
        mimeType: 'text/plain',
        attachmentsPattern: '',
        attachments: [
            [$class: 'ArtifactManagerBuildSelector'],
            [$class: 'StringBuildSelector', stable: true],
            [$class: 'FilePathBuildSelector'],
            [
                'fileName': attachmentFileName,
                'content': attachmentContent.getBytes(),
                'contentType': 'text/plain'
            ]
        ]
    )
}
