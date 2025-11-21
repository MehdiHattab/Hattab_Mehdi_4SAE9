pipeline {
    agent any

    tools {
        maven "M2_HOME"
    }

    stages {

        stage('Code Checkout') {
            steps {
                git branch: 'main',
                url:'https://github.com/MehdiHattab/Hattab_Mehdi_4SAE9.git'
            }
        }

        stage('Build & Test') {
            steps {
                sh "mvn test"
            }
        }

        stage('Code Build') {
            steps {
                sh "mvn package"
            }
        }
    }
}