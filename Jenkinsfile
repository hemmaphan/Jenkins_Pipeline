pipeline {
    // Define the execution environment (replace with your desired agent)
    agent any

    stages {
        stage("Build") {
            steps {
                echo "Building..."
                // Assuming your build commands here (or reference your batch file)
            }
                // Post actions to be executed after all stages
            post {
                always {
                    mail to: "art.random.email@gmail.com", 
                    subject: "Build Status Email", 
                    body: "Build log attached!."
                }
                failure {
                    echo "Build Failed!"
                }
            }
        }
        // Add other stages if needed...
            stage("Test") {
                steps {
                    echo "Testing..."
                    // Assuming your build commands here (or reference your batch file)
                }
            }
            stage("Deploy") {
                    steps {
                        echo "Deploying..."
                        // Assuming your build commands here (or reference your batch file)
                    }
            }
    }
}
