pipeline {
    agent any
 
    environment {
        DIRECTORY_PATH = "/path/to/code"
        TESTING_ENVIRONMENT = "test-env"
        PRODUCTION_ENVIRONMENT = "production-env"
    }
 
    stages {
        stage('Build') {
            steps {
                echo "Fetching the source code from the directory path: ${env.DIRECTORY_PATH} using Maven"
                echo "Compiling the code and generating necessary artifacts"
            }
        }
 
        stage('Unit and Integration Tests') {
            steps {
                echo "Running unit tests"
                sleep(time: 10, unit: 'SECONDS')
                echo "Running integration tests"
            }
        }
 
        stage('Art Added Stage') {
            steps {
                echo 'Art Added Stage.'
            }
            post {
                success {
                    emailext subject: 'Art Added Stage - now using your credentials Saloni',
                        body: 'Art Added Stage',
                        to: 'salonivinodmehta@gmail.com, art.random.email@gmail.com',
                        attachLog: true
                }
            }
        }
 
        stage('Security Scan') {
            steps {
                echo "Performing a security scan on the code using OWASP ZAP or another security scanning tool"
                // Add security scanning step here
            }
        }
 
        stage('Deploy to Staging') {
            steps {
                echo "Deploying the application to a staging server in AWS Elastic Beanstalk"
                // Add deployment to staging step here
            }
        }
 
        stage('Integration Tests on Staging') {
            steps {
                script {
                    echo "Running integration tests on the staging environment to ensure the application functions as expected in a production-like environment"
                    // Create a custom message file
                    writeFile file: 'custom_message.txt', text: 'The Jenkins pipeline has completed successfully.'
                }
            }
            post {
                success {
                    // Archive the custom message file as an artifact
                    archiveArtifacts artifacts: 'custom_message.txt', allowEmptyArchive: true
 
                    // Send notification email for successful pipeline
                    emailext (
                        subject: "Pipeline Status: SUCCESS -- see how there is no attachment?",
                        body: "The Jenkins pipeline has completed successfully.",
                        to: "salonivinodmehta@gmail.com, art.random.email@gmail.com",
                        mimeType: 'text/html'
                    )
                }
            }
        }
 
        stage('Deploy to Production') {
            steps {
                echo "Deploying the code to production environment: ${env.PRODUCTION_ENVIRONMENT}"
                // Add deployment to production step here
            }
        }
    }
}
