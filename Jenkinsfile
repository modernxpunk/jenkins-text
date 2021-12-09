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
                    image 'alpine'
                    args '-=\"root\"'
                }
            }
            steps {
                sh "apk add --update python3 py-pip"
                sh "pip install xmlrunner"
                sh "python3 main.py"
            }
            post {
                always {
                    junit "test-reports/*.xml"
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