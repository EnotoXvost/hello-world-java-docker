pipeline {
    agent {
        any {
            image 'maven:latest'
            args '-v $HOME/.m2:/root/.m2'
        }
    }

    environment {
        MAVEN_OPTS = '-Dmaven.repo.local=.m2/repository'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Maven compile started'
                sh 'mvn compile $MAVEN_OPTS'
            }
        }

        stage('Test') {
            steps {
                echo 'Maven test started'
                sh 'mvn test $MAVEN_OPTS'
            }
        }

        stage('Package') {
            steps {
                echo 'Maven packaging started'
                sh 'mvn package $MAVEN_OPTS'
                sh 'rm -rf build'
                sh 'mkdir -p build'
                sh 'cp target/*.jar build/my-app.jar'
            }
        }

        stage('Deploy') {
            when {
                branch 'master'
            }
            steps {
                echo 'Maven deploy is started for master branch'
            }
        }
    }
    post {
        success {
            archiveArtifacts artifacts: 'build/my-app.jar', fingerprint: true
        }
    }
}
