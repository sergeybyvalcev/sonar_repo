pipeline
{
    agent {
        label '1c'
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
        stage("Hello") {
            steps {                
                bat "chcp 65001\n echo Hello world"
            }
        }          
    }
}