// pipeline {
//   agent any  
 
//   stages {
//     stage('Scan') {
//       steps {
//         withSonarQubeEnv(installationName: 'sonarqube-server') { 
//            sh "mvn sonar:sonar"
//         }
//       }
//     }
//   }
// }

pipeline {
    agent any
    tools { 
      maven 'MAVEN_HOME' 
      jdk 'JAVA_HOME' 
    }
    stages {
      stage ('Build') {
        steps {
          sh 'mvn -B -ntp -Dmaven.test.failure.ignore verify'
        }
      }

    }
}
