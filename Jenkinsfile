pipeline {
    // agent any
    // triggers {
    //     pollSCM 'H/1 * * * *'
    // }
    stages {
        stage('Test') {
            steps {
                sh 'make test'
            }
        }
        stage('Build') {
            steps {
                sh 'make build'
            } 
        }
        stage('Deploy') {
            steps {
                sh 'make deploy'
            }
        }
        stage('Release') {
            steps {
                sh 'make deploy'
            }
        }
    }
}
