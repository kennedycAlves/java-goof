

pipeline {
  agent any  
  stages {
           stage('SonarQube analysis') {
    def scannerHome = tool 'sonar-scanner';
    withSonarQubeEnv('sonarqube-server') { // If you have configured more than one global server connection, you can specify its name
      sh "${scannerHome}/bin/sonar-scanner"
    }
  }
}
}
