pipeline {
  agent any  
  tool name: 'maven' type: 'maven'
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
  }
  stages {
    stage('Scan') {
      steps {
        withSonarQubeEnv(installationName: 'sonarqube-server') { 
          sh './mvnw clean org.sonarsource.scanner.maven:sonar-maven-plugin:3.9.0.2155:sonar'
        }
      }
    }
  }
}
