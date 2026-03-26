pipeline {
  agent any 
  environment {
    IMAGE_NAME = "devops-day13-app"
    VERSION = "v3"
    CCONTAINER_NAME = "devops-day13-app ."
  }
  stages {
    stage ('Clone Code') {
      steps{
        checkout scm
      }
    }
    stage ('Stop Old Container') {
      steps{
        bat 'docker stop %CONTAINER_NAME% || exit 0'
        bat 'docker rm %CONTAINER_NAME% || exit 0'
      }
    }
    stage ('Build Docker Image') {
      steps{
        bat 'docker build -t %IMAGE_NAME%:%VERSION% .'
      }
    }
    stage('Docker Run') {
      steps { 
        
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
