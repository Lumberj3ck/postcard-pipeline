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
                        branch: 'test_dev',
                        url: 'git@github.com:Lumberj3ck/valentiny_api.git'
                }
            }
        }
        stage('Test') {
            steps {
                dir ('project/app'){
                    sh 'envsubst < .env.template > .env'
                    sh 'envsubst < .env.api.template > .env.api'
                    sh 'ls'
                    sh 'cat .env'
                    sh 'cat .env.api'
                }
                dir('project'){
                    sh 'docker compose up -d --build'
                    sh 'docker exec web pytest'
                }
            }
        }
        stage('Build') {
            steps {
                sh 'make build'
                //  go to server run docker compose stop if it is running
                // git pull code base
                // docker install if not installed
                // create env variables on the server using ansible
                // envsubst populate .env
                // build using docker compose and run
            } 
        }
        stage('Deploy') {
            steps {
                sh 'make deploy'
            }
        }
    }
}


