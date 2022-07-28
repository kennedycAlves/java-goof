pipeline {
  agent any  
  stages {
    stage('Scan') {
      steps {
         withSonarQubeEnv('sonarqube-server') { 
          sh '''
          
          dotnet-sonarscanner begin /k:"proyject-key"
          dotnet build solution.sln
          dotnet-sonarscanner end
        
        '''
        }
      }
    }
  }
}


