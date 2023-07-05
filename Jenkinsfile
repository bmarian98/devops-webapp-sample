pipeline {
    agent {
        docker {
            image 'maven:3.8.3-openjdk-17'
            args '-v /var/run/docker.sock:/var/run/docker.sock'
        }
    }
    options {
        skipStagesAfterUnstable()
    }
    stages {
         stage('Clone repository') {
            steps {
                script {
                    checkout scm
                }
            }
        }

        stage('Run Unit Tests'){
            steps {
                script {
                    sh 'mvn test'
                }
            }
        }

        stage('Compile Maven Code'){
            steps {
                script {
                    sh 'mvn -B package'
                }
            }
        }

        stage('Build docker image') {
            steps {
                script {
                    app = docker.build("devops-webapp-sample-bm")
                }
            }
        }
    }
}