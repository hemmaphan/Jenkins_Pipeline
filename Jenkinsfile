pipeline{
      agent any
      environment{
            STAGING_ENVIRONMENT= "AWS EC2 instance"
      }
      stages{
            stage('Build'){
                  steps{
                        echo "This code is built by an automation tool - Maven"
                  }
            }
            stage('Unit Test'){
                  steps{
                        echo "Unit test running ..."
                  }
                  post{
                        success{
                              mail to: "art.random.email@gmail.com",
                              subject: "Unit Test Status Email",
                              body: "Unit test has been run by using test automation tool - Katalon"
                        }
                  }
            }
            stage('Code Analysis'){
                  steps{
                        echo "Quality of the code has been checked by code analysis tool - PMD"
                  }
            }
            stage('Security Scan'){
                  steps{
                        echo "Scanning ..."
                  }
                  post{
                        success{
                              mail to: "art.random.email@gmail.com",
                              subject: "Security Scan Status Email",
                              body: "A security scan on the code has been scanned by OWASP ZAP"
                        }
                  }     
            }
            stage('Deploy to Staging'){
                  steps{
                        echo "The application has been deployed to a staging server - AWS EC2 instance"
                  }
            }
            stage('Integration Test'){
                  steps{
                        echo "Integration test on the $STAGING_ENVIRONMENT has been run by using test automation tool - Katalon"
                  }
            }
            stage('Deploy to Production'){
                  steps{
                        echo "The application has been deployed to a production server - AWS EC2 instance"
                  }
            }

            post {
                always {
                    emailext subject: "Pipeline Status: ${currentBuild.result}",
                             body: "The pipeline has completed with status: ${currentBuild.result}",
                             to: "art.random.email@gmail.com",
                             attachLog: true
                }
            }
        }
    }
