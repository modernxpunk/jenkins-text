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
        stage("Build") {
            steps {
                echo "Building...${BUILD_NUMBER}"
                echo "Build completed"
            }
        }
        stage("Test") {
            agent {
                docker {
                    image: 'alpine'
                    args: '-=\"root\"'
                }
            }
            steps {
                sh "apt-get install python3 python3-pip"
                sh "pip3 install xmlrunner"
                sh "python3 main.py"
            }
            post {
                always {
                    junit allowEmptyResults: true
                    testResults: '**/test-results/*.xml'
                }
                success {
                    echo "testing completed"
                }
                failure {
                    echo "holy..."
                }
            }
        }
    }
}