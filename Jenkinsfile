pipeline {
  agent any  
 
  stages {
    stage('Scan') {
      steps {
        withSonarQubeEnv(installationName: 'sonarqube-server') { 
           sh "mvn sonar:sonar"
        }
      }
    }
  }
}
