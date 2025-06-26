pipeline{
  agent any
  environment{
    IMAGE_NAME = 'ghanashyamauti/test-flask'
  }
  stages{
    stage('Checkout git'){
      steps{
        git branch: 'main', url: 'https://github.com/ghanashyamauti/test-flask'
      }
    }
    stage('Building Docker Image'){
      steps{
        bat "docker built -t %IMAGE_NAME%:latest ."
      }
    }
    stage('Push TO Dockerhub'){
      steps{
        withCredentials([usernamePassword(credentialsID :"Docker", usernameVariable :"ghanashyamauti", passwordVariable :"Kausai@123")])
      }
    }
  }
}
