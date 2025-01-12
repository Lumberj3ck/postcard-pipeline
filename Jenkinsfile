pipeline {
    agent any
    // triggers {
    //     pollSCM 'H/1 * * * *'
    // }
    stages {
        stage('Clone') {
            steps {
                dir('project') {
                    git credentialsId: '7e858f29-ac2f-433d-bd5a-6e1485c1d35a',
                        branch: 'main',
                        url: 'git@github.com:Lumberj3ck/valentiny_api.git'
                }
            }
        }
        stage('Test') {
            steps {
                dir('project'){
                    sh 'docker build . -t postcard-api'
                    sh 'docker run  -p 5000:80 --rm --name postcard-api postcard-api'
                    sh 'docker exec postcard-api pytest'
                }
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
