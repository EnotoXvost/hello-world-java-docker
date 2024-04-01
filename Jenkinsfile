



pipeline { 
   agent any 

   stages {
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
