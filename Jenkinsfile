pipeline {
  agent any  
  stages {
    stage('Scan') {
      steps {
         withSonarQubeEnv('sonarqube-server') { 
          sh '''
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


