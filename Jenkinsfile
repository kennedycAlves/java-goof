pipeline {
  agent any  

  stages {
    stage('Build'){
            steps{
              
                sh '''
                export MAVEN_HOME=/opt/maven
                export PATH=$PATH:$MAVEN_HOME/bin
                mvn --version
                mvn clean package
                '''
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
