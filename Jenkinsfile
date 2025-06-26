pipeline {
  agent any
  environment {
    IMAGE_NAME = 'ghanashyamauti/test-flask'
  }
  stages {
    stage('Checkout git') {
      steps {
        git branch: 'main', url: 'https://github.com/ghanashyamauti/test-flask'
      }
    }
    stage('Building Docker Image') {
      steps {
        bat "docker build -t %IMAGE_NAME%:latest ."
      }
    }
    stage('Push TO Dockerhub') {
      steps {
        withCredentials([usernamePassword(credentialsId: 'Docker', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
          bat """
          echo %DOCKER_PASS% | docker login -u %DOCKER_USER% --password-stdin
          docker push %IMAGE_NAME%:latest
          docker logout
          """
        }
      }
    }
  }
}
