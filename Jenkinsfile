pipeline {
  agent any  

  stages {
    stage('Build'){
            steps{
              
                sh "env.MAVEN_HOME = '${tool 'maven-3.8.6'}'"
                
                sh 'mvn clean package'
               
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
