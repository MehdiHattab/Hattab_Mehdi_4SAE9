pipeline {
    agent any

    tools {
        maven "M2_HOME"
    }

    environment {
        DOCKER_CREDENTIALS= credentials('dockerhub')
    }

    stages {
        stage("Code Checkout") {
            steps {
                git branch: 'main',
                    url: 'https://github.com/MehdiHattab/Hattab_Mehdi_4SAE9.git'
            }
        }

        stage('Code Test') {
            steps {
                sh "mvn test"
            }
        }

        stage('Code Build') {
            steps {
                sh "mvn package"
            }
        }

        stage('Sonar Test'){
            steps {
                withSonarQubeEnv('SQ1') {
                    sh "mvn sonar:sonar"
                }
            }
        }

        stage('Docker Build') {
            steps {
                script {
                    sh "docker build -t hattabmehdi/student-management:1.0 ."
                }
            }
        }

        stage('Docker Push') {
            steps {
                script {
                    sh 'echo $DOCKER_CREDENTIALS_PSW | docker login -u $DOCKER_CREDENTIALS_USR --password-stdin'
                    sh "docker push hattabmehdi/student-management:1.0"
                }
            }
        }
    }
}
