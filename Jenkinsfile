/*pipeline {
    options {timestamps()}
    
    agent { docker { image 'python:3.10.1-alpine' } }

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
}*/

pipeline {
  agent { docker { image 'python:3.10.1-alpine' } }
  stages {
    stage('foo') {
      steps {
        sh "python --version"
      }
    }
  }
}