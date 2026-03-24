pipeline {
  agent any 
  stages {
    stage ('Clone Code') {
      steps{
        checkout scm
      }
    }
    stage ('Build Docker Image') {
      steps{
        bat 'docker build --no-cache -t devops-day13-app .'
      }
    }
    stage('Test Container') {
      steps { 
        bat 'docker stop devops-day13-app container || exit 0 '
        bat 'docker remove devops-day13-app container || exit 0'
        bat 'docker run -d -p 8085:80 devops-day13-app'
      }
    }
    stage('Verify Running Container') {
      steps {
        bat 'docker ps'
      }
    }
  }
}
