pipeline {
    agent {
        docker {
            image 'node:12-alpine'
        }
    }
    environment {
      HOME = "."
      CI = true
    }
    stages {
        stage('Install') {
            steps {
              sh 'npm i'
            }
        }
        stage("test"){
            steps{
                sh "npm test"
            }
            post{
                always{
                    echo "====++++always++++===="
                }
                success{
                    echo "====++++test executed successfully++++===="
                }
                failure{
                    echo "====++++test execution failed++++===="
                }

            }
        }
    }
    post {
        failure {
            echo 'mail to: team@example.com, subject: "The Pipeline failed :("'
        }
    }
}