pipeline {
  agent any  

  stages {
    stage('Build'){
            steps{


              
                // sh "export MAVEN_HOME= '${tool 'maven'}'"
                sh '''
                
                export MAVEN_HOME=/var/jenkins_home/tools/hudson.tasks.Maven_MavenInstallation/maven
                export PATH=$PATH:$MAVEN_HOME/bin
                mvn clean package
                
                export SONAR_HOME=/var/jenkins_home/tools/hudson.plugins.sonar.SonarRunnerInstallation/sonar-scanner/
                export PATH=$PATH:$SONAR_HOME/bin
            
               mvn sonar:sonar -X -e \
                  -Dsonar.projectKey=teste \
                  -Dsonar.host.url=http://192.168.100.115:9000 \
                  -Dsonar.login=75ccf04de4df3fbb7a9741324cf8936cf6ec91e9
                
                 '''
                //   -Dsonar.projectKey=maven-token \
                //   -Dsonar.host.url=http://127.0.0.1:9000 \
                //   -Dsonar.login=1982250f39c4e5105d8e57ac20e64746f5eead85
                
               
               
            }
         }
    // stage('Scan') {
    //   steps {
    //      withSonarQubeEnv('sonarqube-server') { 
    //       sh '''
           
    //       '''

    //     }
    //   }
    // }
  }
}
