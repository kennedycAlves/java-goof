pipeline {
  agent any  
  tools {
    maven 'Maven 4.0.0'
    jdk 'jdk8'
  }
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

