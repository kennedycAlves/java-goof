

pipeline {
  agent any  
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
  }
  stages {
    stage('Scan') {
      steps {
        withSonarQubeEnv(installationName: 'sonar') { 
          sh '''
            	sonar-scanner \
                -Dsonar.projectKey=jenkins \
                -Dsonar.sources=. \
                -Dsonar.host.url=http://127.0.0.1:9000 \
                -Dsonar.login=7fbc16826bceb1201dbb0bf135c50ac3aa47cd9f
          '''
        }
      }
    }
  }
}
