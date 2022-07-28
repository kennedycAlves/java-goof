pipeline {
  agent any  
  stages {
    stage('Scan') {
      steps {
        scannerHome = tool 'sonar-scanner';
         withSonarQubeEnv('sonarqube-server') { 
          sh "${scannerHome}/bin/sonar-scanner"
        }
      }
    }
  }
}


