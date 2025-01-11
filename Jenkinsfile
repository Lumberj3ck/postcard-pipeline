pipeline {
    agent any
    // triggers {
    //     pollSCM 'H/1 * * * *'
    // }
    stages {
        stage('Clone') {
            steps {
                sh 'ls'
                sh 'mkdir project -p'
                sh 'cd project'
                sh 'ls'
                git credentialsId: '7e858f29-ac2f-433d-bd5a-6e1485c1d35a',
                    branch: 'main',
                    url: 'git@github.com:Lumberj3ck/valentiny_api.git'
                sh 'cd ..'
                sh 'ls'
            }
        }
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
                sh 'make release'
            }
        }
    }
}
