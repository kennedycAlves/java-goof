pipeline {
  agent any  
  
  environment {
         MAVEN_HOME = tool name: 'maven'                   
         SONAR_HOME =  tool name: 'sonar-scanner'
    }

  stages {
    stage('Build'){
            steps{
           
                sh 'echo export MAVEN_HOME= "{env.$MAVEN_HOME}"'
               
                sh'''
                
                export PATH=$PATH:$MAVEN_HOME/bin
                mvn clean package
                
                
                 '''

            }
         }
         
    stage('Scan') {
      steps {
         withSonarQubeEnv('sonarqube-server') { 
             
            sh 'echo export MAVEN_HOME= "{env.$MAVEN_HOME}"' 
            sh 'echo export SONAR_HOME= "{env.$SONAR_HOME}"'   
            sh '''
        
                    export PATH=$PATH:$SONAR_HOME/bin
                    export PATH=$PATH:$MAVEN_HOME/bin
                
                    mvn sonar:sonar -X -e \
                      -Dsonar.projectKey=jenkins \
                      -Dsonar.host.url=http://192.168.100.115:9000 \
                      -Dsonar.login=e1e3b33ff25592a3f02aaa4522c31b5881bb671c
              '''

        }
      }
    }
  }
}
