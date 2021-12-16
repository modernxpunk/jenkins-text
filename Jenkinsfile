pipeline {
    options {timestamps()}
    
    stages {
        stage("Check scm") {
            agent any
            steps {
                checkout scm
            }
        }
        stage('build') {
            steps {
                sh 'python --version'
            }
        }
    }
}