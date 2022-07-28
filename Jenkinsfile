

pipeline {
  agent any  
  stages {
          stage('SAST') {
              environment {
                  SCANNER_HOME = tool 'sonar-scanner'
              }
              steps {
                  withSonarQubeEnv('sonarqube-server') {
                      sh" ${SCANNER_HOME}}/bin/sonar-scanner \
                      -Dsonar.projectKey=simple_webapp \
                      -Dsonar.sources=. "
                  }
              }
          }
      }
}
