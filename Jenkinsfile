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

        stage ('Print msg on test branch'){
            when{
                    branch 'test'
                }
            steps {
                script{
                    sh 'echo I\'m on test branch'
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