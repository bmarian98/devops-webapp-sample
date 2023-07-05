pipeline {
    agent {
        node {
            label 'centos-1'
        }
    }
    options {
        skipStagesAfterUnstable()
    }
    stages {
         stage('Clone repository') {
            steps {
                script{
                    checkout scm
                }
            }
        }

        stage('Run Unit Tests'){
            step{
                script{
                    sh 'mvn test'
                }
            }
        }

        stage('Compile Maven Code'){
            step{
                script{
                    sh 'mvn test'
                }
            }
        }

        stage('Build') {
            steps {
                script{
                    app = docker.build("devops-webapp-sample-bm")
                }
            }
        }
    }
}