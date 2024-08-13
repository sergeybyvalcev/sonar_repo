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
                bat "echo Сообщение из steps"
                bat "echo переменная envString = ${envString}"
            
                script {
                    scannerHome = tool "sonar-scanner"
                }
            }
        }    
    }
}