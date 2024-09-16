pipeline {
    agent any 
    environment {
        DIRECTORY_PATH = "/Users/lachl/OneDrive/Desktop/Uni/Y2 T2/SIT223 Professional Practice"
        TESTING_ENVIRONMENT = "Pipeline (test Environment)"
        PRODUCTION_ENVIRONMENT = "Lachlan Cooper"
    }
    stages {
        stage('Build') {
            steps {
                echo "Build using maven"
                echo "compile the code and generate any necessary artifacts"
            }
        }
            
        stage('Test') {
            steps {
                echo "Unit tests"
                echo "integration tests using rational integration tester"
            }
            post {
                always {
                    script {
                        sendEmailNotification('Test', currentBuild.result)
                    }
                }
            }
        }

        stage('Code Analysis') {
            steps {
                echo "code analysis tool: codacy"
            }
        }

        stage('Security Scan') {
            steps {
                echo "Code scan using Codesecure"
            }
            post {
                always {
                    script {
                        sendEmailNotification('Security Scan', currentBuild.result)
                    }
                }
            }
        }
        
        stage('Deploy to Staging') {
            steps {
                echo " AWS EC2 Instance"
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo "runs integration tests on the environment"
            }
        }
        
        stage('Deploy to Production') {
            steps {
                echo "Code deployed in AWS EC2 Instance"
            }
        }
    }
}

def sendEmailNotification(stageName, buildStatus) {
    emailext (
        subject: "${stageName} Stage - Build ${buildStatus}",
        body: """\
            Hi Team,

            The ${stageName} stage has completed with the status: ${buildStatus}.

            Please find the attached logs for more details.

            Regards,
            Jenkins
        """,
        to: 's223362503@deakin.edu.au',
        attachLog: true,
        compressLog: true
    )
}
