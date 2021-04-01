pipeline {
    agent any
    stages {
        stage('Install') {
            steps {
              echo 'TODO: install other part if needed'
            }
        }
        stage('Build1') {
            when {
                anyOf {
                  branch 'release/dev';
                  branch 'release/uat';
                  branch 'master';
                }
            }
            steps {
                echo 'npm run deploy:prepare'
            }
        }
        stage('Build2') {
            when {
                expression {
                    currentBuild.result == null || currentBuild.result == 'SUCCESS'
                }
            }
            steps {
                echo 'npm run deploy:prepare'
            }
        }
        stage('Build') {
            when {
              allOf {
                anyOf {
                  branch 'release/dev';
                  branch 'release/uat';
                  branch 'master';
                }
                expression {
                  currentBuild.result == null || currentBuild.result == 'SUCCESS'
                }
              }
            }
            steps {
                echo 'npm run deploy:prepare'
            }
        }
    }
    post {
        failure {
            echo 'mail to: team@example.com, subject: "The Pipeline failed :("'
        }
    }
}