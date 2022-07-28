

pipeline {
  agent any  
  stages {
          stage('SAST') {
              environment {
                  SCANNER_HOME = tool 'sonar-scanner'
              }
              steps {
                  withSonarQubeEnv('sonarqube-server') {
                      sh" 	sonar-scanner \
                            -Dsonar.projectKey=jenkins \
                            -Dsonar.sources=. \
                            -Dsonar.host.url=http://127.0.0.1:9000 \
                            -Dsonar.login=7fbc16826bceb1201dbb0bf135c50ac3aa47cd9f"
                  }
              }
          }
      }
}
