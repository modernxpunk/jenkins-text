pipeline {
    options {timestamps()}
    
    agent none

    stages {
        stage("Check scm") {
            agent any
            steps {
                checkout scm
            }
        }
        stage('build') {
            agent {
                docker {
                    image 'alpine'
                    args '-u=\"root\"'
                }
            }
            steps {
                sh 'python main.py'
            }
            post {
                success {
                    echo "finally..."
                }
                failure {
                    echo "what? ?!?!? !?"
                }
            }
        }
    }
}