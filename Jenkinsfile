pipeline {
  agent any 
  stages{
    stage('Pull Code') {
      steps {checkout scm}
    }
    stage('Build Docker Image') {
      steps {
        bat 'Docker build -t devops-day13-app .'
      }
    }
    stage('Run Container') {
      steps {
        bat 'Docker run -d -p 8085:80 Devops-day13-app'
      }
    }
    stage('Check Running Containers') {
      steps {
        bat 'Docker ps'
      }
    }
  }
}
