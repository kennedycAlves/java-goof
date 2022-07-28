pipeline {
  agent any  

  stages {
    stage('Build'){
            steps{
                sh 'maven clean package'
            }
         }
    stage('Scan') {
      steps {
         withSonarQubeEnv('sonarqube-server') { 
          sh "maven sonar:sonar"

        }
      }
    }
  }
}
