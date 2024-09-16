pipeline{
    agent any 
    environment {
        DIRECTORY_PATH = "/Users/lachl/OneDrive/Desktop/Uni/Y2 T2/SIT223 Professional Practice"
        TESTING_ENVIRONMENT = "Pipeline (test Environment)"
        PRODUCTION_ENVIRONMENT = "Lachlan Cooper"
    }
    stages{
        stage('Build'){
            steps{
                echo "fetch the source code from the directory path specified by the environment variable"
                echo "comple the code and generate any neccessary artifacts"
            }
        }
            
        stage('Test'){
            steps{
                echo "Unit tests "
                echo "integration tests"
            }
        }

        stage('Code'){
            steps{
                echo "check the quality of the code "
            }
        }

        stage('Deploy'){
            steps{
                echo "Deploy the application to a testing environment specificed by the environment variable"
            }
        }
        
        stage('Approval'){
            steps{
                sleep(10)
            }
        }

        stage('Deploy to Production'){
            steps{
                echo "Code deployed in $TESTING_ENVIRONMENT"
            }
        }
    }
    
}
