pipeline {
    options {timestamps()}
    
    agent any

    stages {
        stage("Check scm") {
            agent any
            steps {
                checkout scm
            }
        }
        stage('build') {
            steps {
                sh 'docker version'
            }
        }
    }
}