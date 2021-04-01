pipeline {
    agent any
    environment {
        CI = 'true'
    }
    stages {
        stage('Installation') {
            steps {
              sh 'npm i'
            }
        }
        stage('Test') {
            steps {
              sh 'npm test'
            }
            post {
              always {
                sh 'echp send coverage'
              }
            }
        }
    }
    post {
        failure {
            echo "mail to: team@example.com, subject: 'The Pipeline failed :('"
        }
    }
}