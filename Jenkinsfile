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
            allure includeProperties: false, jdk: '', results: [[path: 'out/syntax-check/allure']]
            junit stdioRetention: '', testResults: 'out/syntax-check/junit/junit.xml'
        }

        failure {
            bat "echo failure"
        }

        success {
            bat "echo succes"
        }

    }
    stages {
        stage("Build test base") {
            steps {                
                bat "chcp 65001\n vrunner init-dev --dt C:\\jenkins\\template\\dev.dt --db-user Teacher --src C:\\repo\\sonar_repo\\src"
            }
        }
        stage("Syntax check") {
            steps {
                bat "chcp 65001\n vrunner syntax-check" 
            }
        }      
    }
}