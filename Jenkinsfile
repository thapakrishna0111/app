pipeline {
    agent any
    stages {
        stage('Verify Branch') {
            steps {
                echo '$GIT_BRANCH'
            }
        }
        stage('Docker build') {
            steps {
                sh 'docker images'
                sh '''cd azure-vote
                docker images -a
                docker build -t jenkins-pipeline .
                docker images -a
                cd ..'''
            }
        }
        stage('start test app') {
            steps {
                sh '''cd scripts/
                ./test_container.sh
                '''
            }
            post {
                success {
                    sh 'echo "App started Sucessfully :)"'
                }
                failure {
                    sh 'echo "App failed :("'
                }
            }
            
        }
        stage('Run Test') {
            steps {
                sh '''cd scripts/
                ./test_container.sh
                cd ..'''
            }
        }
        stage('stop test app') {
            steps {
                sh 'docker-compose down'
            }
        }

    }
}
