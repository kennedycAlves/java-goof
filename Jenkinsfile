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
                  -Dsonar.projectKey=jenkins \
                  -Dsonar.host.url=http://127.0.0.1:9000 \
                  -Dsonar.login=e1e3b33ff25592a3f02aaa4522c31b5881bb671c
                
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
