pipeline {
    agent {
        docker {
            image 'node:12-alpine'
        }
    }
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
              sh 'echo test'
            }
            post {
              always {
                sh 'echo send coverage'
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