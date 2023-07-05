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
                    echo "I'm on test branch"
                }
            }
        }
    }
}