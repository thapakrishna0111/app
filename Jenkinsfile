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
                cd script/
                ./test_container.sh
            }
            post {
                success {
                    echo "App started Sucessfully :)"
                }
                failure {
                    echo "App failed to start :("
                }
            }
            
        }
        stage('Run Test') {
            steps {
                sh '''cd script/
                ./test_container.sh
                '''
            }
        }
    }
}
