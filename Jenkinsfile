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
        stage("Smoke tests") {
            steps {
                script {
                    try {
                        bat "chcp 65001\n runner xunit"
                    }
                    catch(Exception Exc) {
                        currentBuild.result = 'UNSTABLE'
                    }
                }                
            }
        } 
         stage("vanessa") {
            steps {
                script {
                    try {
                        bat "chcp 65001\n runner vanessa"
                    }
                    catch(Exception Exc) {
                        currentBuild.result = 'UNSTABLE'
                    }
                }                
            }
        }       
    }
}