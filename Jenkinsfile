pipeline {
  agent any  
  stages {
    stage('Scan') {
      steps {
        def scannerHome = tool 'sonar-scanner';
         withSonarQubeEnv('sonarqube-server') { 
          sh "${scannerHome}/bin/sonar-scanner"
        }
      }
    }
  }
}


