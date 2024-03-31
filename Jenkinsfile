pipeline {
   
   agent any
   
   stages {
       stage('Run docker image') {
           
          steps{
             echo 'Run'
          }
       }

      stage('Build docker image') {
           steps{
             echo 'build'  
             script { 
                   sh 'docker build -t hello-world-java-docker .' 
               } 
          }
       }

      stage('Stop docker image') {
           steps{
             echo 'stop'
          }
       }
   }
  
post { 
       success { 
           archiveArtifacts artifacts: 'target/*.jar', fingerprint: true         
       } 
   } 
}
}

