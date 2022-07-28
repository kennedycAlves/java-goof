pipeline {
  agent any  
  stages {
    stage('Build'){
            steps{
                sh 'mvn clean package'
            }
         }
    stage('Scan') {
      steps {
         withSonarQubeEnv('sonarqube-server') { 
          sh "mvn sonar:sonar"

        }
      }
    }
  }
}
