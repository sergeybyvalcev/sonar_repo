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
            allure includeProperties: false, jdk: '', results: [[path: 'out/syntax-check/allure'], [path: 'out/smoke/allure/'], [path: 'build/reports/allurereport/1С']]
            junit allowEmptyResults: true, stdioRetention: '', testResults: 'out/syntax-check/junit/junit.xml'
            junit allowEmptyResults: true, stdioRetention: '', testResults: 'out/smoke/junit/*.xml'
            junit allowEmptyResults: true, stdioRetention: '', testResults: 'build/reports/junitreport/*.xml'
        }

        failure {
            bat "echo failure"
        }

        success {
            bat "echo succes"
        }

    }
    stages {        
        stage("sonar") {
            steps {
                script {
                    scannerHome = tool 'sonar-scanner'

                } 
                withSonarQubeEnv("sonar") {
                    bat "${scannerHome}/bin/sonar-scanner -D sonar.login=sqp_6cf38cd50ccb930822ff8064595029c8c08dabe0 -D sonar.projectVersion=${BUILD_ID}"
                }                   
            }
        }       
    }
}