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
            steps {
                script {
                    docker.image('maven:3.6.3-openjdk-17').inside{
                        sh 'mvn test'
                        }
                }
            }
        }

        stage('Compile Maven Code'){
            steps {
                script {
                    docker.image('maven:3.6.3-openjdk-17').inside{
                        sh 'mvn -B package'
                    }
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
