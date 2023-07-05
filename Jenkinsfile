pipeline {
    agent {
        label 'centos-3'
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

        stage('Install maven'){
            steps {
                script {
                    sh 'yum install -y maven'
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
                    sh 'mvn test'
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    app = docker.build("devops-webapp-sample-bm")
                }
            }
        }
    }
}