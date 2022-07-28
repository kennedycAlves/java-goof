pipeline {
  agent any  
  stages {
    stage('Scan') {
      steps {
         withSonarQubeEnv('sonarqube-server') { 
         sh 'mvn clean package sonar:sonar'

        }
      }
    }
  }
}


