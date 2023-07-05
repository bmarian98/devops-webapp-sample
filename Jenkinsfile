pipeline {
    agent {
        label 'docker'
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
            agent {
                docker {
                    image 'maven:3.6.3-openjdk-17'
                }
            }
            steps {
                script {
                    sh 'mvn test'
                }
            }
        }

        stage('Compile Maven Code'){
            agent {
                docker {
                        image 'maven:3.6.3-openjdk-17'
                        }
            }
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
