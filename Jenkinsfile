pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                echo "Fetch the source code from the directory: "
            }
        }
        
        stage('Unit and Integration Tests') {
            steps {
                echo "Conduct integration tests to make sure Cucumber can communicate with all of the application's components."
            }
            post {
    success {
        emailext (
            to: "ruthvikbeeram@gmail.com",
            subject: "Build status",
            body: "Test was successful and logs were attached",
            attachLog: true
        )
    }
    failure {
        emailext(
            to: "ruthvikbeeram@gmail.com",
            subject: "Build Status",
            body: "Test Failed and logs were attched",
            attachLog: true
        )
    }
}

        }
        
        stage('Code Analysis') {
            steps {
                 echo "- include a code analysis programme that uses Fortify to examine the code and make sure it complies with industry requirements"
            }
        }
        
        stage('Security Scan') {
            steps {
                echo "to find any vulnerabilities, run a Qualys security scan on the code."
            }
            post {
                success{
		 emailext(
                    to:"ruthvikbeeram@gmail.com",
                    subject:"Build Status" ,
                    body: "Scan was successful",
		    attachLog: true
			)
                }
                failure{
			emailext(
                    to:"ruthvikbeeram@gmail.com",
                    subject:"Build Status",
                    body: "Scan Failed and the logs were attached",
                    attachLog : true
			)
                }
            }
        }
        
        stage('Deploy to Staging') {
            steps {
               echo "Use CircleCI to deploy the application to a staging server."
             }
        }
        
        stage('Integration Tests on Staging') {
            steps {
                 echo " Using Cypress to run integration tests on the staging environment to make sure the application performs as anticipated"
            }
        }
        
        stage('Deploy to Production') {
            steps {
               echo "Docker Swarm is used to deploy the code to a production environment."
            }
        }
    }
    
}
