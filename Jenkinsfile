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
   stage('Dependency Check Report') {
    steps {
        dependencyCheck additionalArguments: ''' 
            -o "./" 
            -s "./"
            -f "ALL" 
            --prettyPrint''', odcInstallation: 'Dependency-Check'
        dependencyCheckPublisher pattern: 'dependency-check-report.xml'
          }    
    }
    
    stage('Send report to DefecDojo') {
        steps {
           
            sh 'cp ../upload-files.py .'
            sh 'chmod +x upload-files.py'
            sh "python3 upload-files.py --result_file /var/lib/jenkins/workspace/Pipeline-Sec/dependency-check-report.xml  --scanner 'Dependency Check Scan' --host 127.0.0.1:8080 --api_key d64dca4d31e577b7924ac6e0b8cc59f4b1526430  --name Namerepository"
                       
           }    
    }
  }
}
