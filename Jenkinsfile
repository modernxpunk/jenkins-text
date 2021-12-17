pipeline {
    options {timestamps()}
    
    agent none

    stages {
        stage("checkout scm") {
            agent any
            steps {
                checkout scm
            }
        }
        state('build') {
            steps {
                echo "building..."
                echo "building completed"
            }
        }
        stage('test') {
            agent {
                docker {
                    image 'alpine'
                    args '-u=\"root\"'
                }
            }
            steps {
                sh '''
                    apk add --update python3 py-pip
                    pip install xmlrunner
                    python3 tests.py
                '''
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