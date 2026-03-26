pipeline {
  agent any 
  environment {
    IMAGE_NAME = "devops-day13-app ."
    VERSION = "v1"
    CCONTAINER_NAME = "devops-day13-app"
  }
  stages {
    stage ('Clone Code') {
      steps{
        checkout scm
      }
    }
    stage ('Build Docker Image') {
      steps{
        bat 'docker build --no-cache -t %IMAGE_NAME%:%VERSION% .'
      }
    }
    stage('Test Container') {
      steps { 
        bat 'docker stop %CONTAINER_NAME% || exit 0'
        bat 'docker rm %CONTAINER_NAME% || exit 0'
        bat 'docker run -d -p 8085:80 %CONTAINER_NAME% %IMAGE_NAME%:%VERSION%'
      }
    }
    stage('Verify Running Container') {
      steps {
        bat 'docker ps'
      }
    }
  }
}
