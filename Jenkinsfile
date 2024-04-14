pipeline {
    // Define the execution environment (replace with your desired agent)
    agent any

    stages {
        stage("Build") {
            steps {
                echo "Building..."
                // Assuming your build commands here (or reference your batch file)
            }
        }
        // Add other stages if needed...
    }

    // Post actions to be executed after all stages
    post {
        success {
            mail to: "art.random.email@gmail.com", 
            subject: "Build Successful!", 
            body: "Build completed successfully."
        }
        failure {
            echo "Build Failed!"
        }
    }
}