pipeline
{
    agent {
        label '1C'
    }

    environment {
        envString = 'true'
    }

    post {
        always {
            bat "echo always"
        }

        failure {
            bat "echo failure"
        }

        success {
            bat "echo succes"
        }

    }
    stages {
        stage("stage") {
            steps {                
                bat "echo Messages from steps"
                bat "echo envString = ${envString}"
            
                script {
                    scannerHome = tool "sonar-scanner"
                }
            }
        }    
    }
}