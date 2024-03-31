ipeline {
   agent any
   stages {
       stage('Build docker image') {
           steps {
               script {
                   echp 'build project'
                   sh 'docker build -t hello-world-java-docker .'
               }
           }
       }
   }
   post {
       always {
           archiveArtifacts artifacts: 'target/*.jar', fingerprint: true        
       }
   }
}
