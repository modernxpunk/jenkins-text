/*pipeline {
    options {timestamps()}
    
    agent { docker { image 'python:3.10.1-alpine' } }

    environment {
        DOCKER_CERT_PATH = credentials('')
    }

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
  agent any
  tools {
    'org.jenkinsci.plugins.docker.commons.tools.DockerTool' '18.09'
  }
  environment {
    DOCKER_CERT_PATH = credentials('/var/jenkins_home/secrets/initialAdminPassword')
  }
  stages {
    stage('foo') {
      steps {
        sh "docker version"
      }
    }
  }
}