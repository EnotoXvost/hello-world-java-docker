pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/EnotoXvost/hello-world-java-docker'
            }
        }

        stage('Build inside Docker') {
            steps {
                script {
                    docker.image('registry.access.redhat.com/ubi8/ubi-minimal:8.5').inside {
                        sh 'docker build -t hello-world-java-docker .'
                        sh 'docker run -it hello-world-java-docker mvn clean package'
                    }
                }
            }
        }

        stage('Archive artifact') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }
    }
}
