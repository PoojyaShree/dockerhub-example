pipeline {
  agent any
  
  environment {
    DOCKERHUB_CREDENTIALS = credentials('DOCKER_CRDS')
  }
  stages {
    stage('Build') {
      steps {
        sh 'docker build -t gaddamnarendra/maven:4 .'
      }
    }
    stage('Login') {
      steps {
        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
      }
    }
    stage('Push') {
      steps {
        sh 'docker push gaddamnarendra/maven:latest'
      }
    }
  }
  post {
    always {
      sh 'docker logout'
    }
  }
}
