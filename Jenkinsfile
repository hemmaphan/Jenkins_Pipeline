pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                // Run your build commands
                // For demonstration purposes, let's echo some content to a log file
                script {
                    // Use echo to write to a file (works on both Windows and Unix-like systems)
                    // This will create a log file named 'build.log' with the specified content
                    bat 'echo Build details... > build.log'
                }
            }
        }
        stage('Unit Test') {
            steps {
                // Run your unit tests
            }
            post {
                success {
                    // Send success email
                }
                failure {
                    // Send failure email
                }
            }
        }
    }
}
