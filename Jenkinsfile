// define uma lista de projetos que passarão pela pipeline
projects = "Java-goof"
//https://github.com/vitoraalmeida/forum
//https://github.com/vitoraalmeida/leilao
node {
    // limpa o workspace para remover arquivos antigos de builds anteriores
    cleanWs()
    stage ('clone repos') {
        // executa um loop para clonar cada repositório da lista num diretório próprio
        // for(project in projects) {
            // dir("${project}") {
                // echo "dentro de ${project}"
                git branch: 'main', url: "https://github.com/kennedycAlves/java-goof"
        //     }
        // }
        sh 'ls'
    }
    // para cada projeto, navega até o diretório clonado e, se for um projeto com Maven (pom.xml)
    // executa o comando do maven que executa o plugin Cyclonedx. Se for gradle, o comando equivalente.
    stage ('execute cyclonedxBom') {
        // for(project in projects) {
            // dir("${project}") {
                if (fileExists('pom.xml')) {
                    withMaven(maven: 'maven') {
                        echo "Executing cyclonedxBom"
                        sh 'mvn org.cyclonedx:cyclonedx-maven-plugin:makeAggregateBom'
                    }
                } else {
                    echo "Executing cyclonedxBom"
                    sh './gradlew cyclonedxBom -info'
                }
        //     }
        // }
    }

    // Utilizando a API key do dependency track, para cada relatório gerado em cada projeto, envia o relatório para o 
    // dependency track criando um novo projeto para o repositório em questão se ele já não existir
    stage('dependencyTrackPublisher') {
        // for(project in projects) {
            // dir("${project}") {
                if (fileExists('./target')) {
                    withCredentials([string(credentialsId: 'dependency-track', variable: 'API_KEY')]) {
                        dependencyTrackPublisher artifact: 'target/bom.xml', projectName: "${project}", projectVersion: '1', synchronous: true, dependencyTrackApiKey: API_KEY
                    }
                } else {
                    withCredentials([string(credentialsId: 'dependency-track', variable: 'API_KEY')]) {
                        dependencyTrackPublisher artifact: 'build/reports/bom.xml', projectName: "${project}", projectVersion: '1', synchronous: true, dependencyTrackApiKey: API_KEY
                    }
                }
        //     }
        // }
    }


// pipeline {
//   agent any  
  
//   environment {
//          MAVEN_HOME = tool name: 'maven'                   
//          SONAR_HOME =  tool name: 'sonar-scanner'
//     }

//   stages {
//     stage('Build'){
//             steps{
           
//                 sh 'echo export MAVEN_HOME= "{env.$MAVEN_HOME}"'
               
//                 sh'''
                
//                 export PATH=$PATH:$MAVEN_HOME/bin
//                 mvn clean package
                
                
//                  '''

//             }
//          }
  
    // stage('Scan') {
    //   steps {
    //      withSonarQubeEnv('sonarqube-server') { 
             
    //         sh 'echo export MAVEN_HOME= "{env.$MAVEN_HOME}"' 
    //         sh 'echo export SONAR_HOME= "{env.$SONAR_HOME}"'   
    //         sh '''
        
    //                 export PATH=$PATH:$SONAR_HOME/bin
    //                 export PATH=$PATH:$MAVEN_HOME/bin
                
    //                 mvn sonar:sonar -X -e \
    //                   -Dsonar.projectKey=jenkins \
    //                   -Dsonar.host.url=http://192.168.100.115:9000 \
    //                   -Dsonar.login=02a034674a8cc59121f69d82c5f5b6d2ece15da7
    //           '''
        
    //     }
    //   }
    // }
   // stage('Dependency Check Report') {
   //  steps {
   //      dependencyCheck additionalArguments: ''' 
   //          -o "./" 
   //          -s "./"
   //          -f "ALL" 
   //          --prettyPrint''', odcInstallation: 'Dependency-Check'
   //      dependencyCheckPublisher pattern: 'dependency-check-report.xml'
   //        }    
   //  }
    
// stage('Wait Quality Gate'){
//             steps {
//                 script {
//                     withSonarQubeEnv("sonarqube-server"){
//                         catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
//                             timeout(time: 1, unit: 'HOURS') {
//                                 waitForQualityGate abortPipeline: false
//                             }
//                         }
//                     }
//                 }
//             }
//         }
    
  //   stage('Send report to DefecDojo') {
  //       steps {
           
  //           sh 'cp ../upload-files.py .'
  //           sh 'chmod +x upload-files.py'
  //           sh "python3 upload-files.py --result_file /var/lib/jenkins/workspace/Pipeline-Sec/dependency-check-report.xml  --scanner 'Dependency Check Scan' --host 127.0.0.1:8080 --api_key d64dca4d31e577b7924ac6e0b8cc59f4b1526430  --name Namerepository"
  //           sh "sonar-report --sonarurl='http://192.168.100.115:9000'  --sonarcomponent='jskey' --project='jskey Project'  -sonartoken='02a034674a8cc59121f69d82c5f5b6d2ece15da7'  --sinceleakperiod='false' --fixMissingRule='true'  --noSecurityHotspot='true'  --allbugs='true' > sonar.html"         
  //           sh "python3 upload-files.py --result_file /var/lib/jenkins/workspace/Pipeline-Sec/sonar.html  --scanner 'SonarQube Scan' --host 127.0.0.1:8080 --api_key d64dca4d31e577b7924ac6e0b8cc59f4b1526430  --name Namerepository"
  //      }         
  //   }
  }
}
