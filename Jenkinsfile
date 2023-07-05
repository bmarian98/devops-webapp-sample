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

        stage ('Print msg on test branch'){
            steps {
                when{
                    branch 'test'
                }
                script{
                    sh 'echo I\'m on test branch'
                }
            }
        }
    }
}