pipeline {
    agent {
        label linux-small
    }
    environment {
        PROJECT_VERSION = "${params.projectVersion?: mvn.version}"
    }
    tools {
       maven params.mavenVersionSetAsParameterInJob
       jdk params.javaVersionSetAsParameter 
       // most of the tools can be controlled this way
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
