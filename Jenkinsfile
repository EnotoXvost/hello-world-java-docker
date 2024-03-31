



pipeline { 
   agent any 
   tools { 
       maven 'maven' 
   } 
   stages { 
       stage('Build Maven') { 
           steps { 
               checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/EnotoXvost/hello-world-java-docker']]]) 
               sh 'mvn clean install' 
           } 
       } 
       stage('Build docker image') { 
           steps { 
               script { 
                   sh 'docker build -t hello-world-java-docker .' 
               } 
           } 
       } 
       
   } 
   post { 
         success { 
           archiveArtifacts artifacts: 'target/*.jar', fingerprint: true         
       } 
   } 
}
