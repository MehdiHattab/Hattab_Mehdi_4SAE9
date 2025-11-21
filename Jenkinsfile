pipeline {
    agent any

    tools {
        maven "M2_HOME"
    }

    stages {

        stage('Maven Version') {
            steps {
                sh "mvn -version"
            }
        }

        stage('Build & Test') {
            steps {
                sh "mvn test"
            }
        }

        stage('Package') {
            steps {
                sh "mvn package"
            }
        }
    }
}