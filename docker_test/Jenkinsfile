pipeline   {
    agent any
    stages {
        stage('Verify Branch') {
            steps {
                echo '$GIT_BRANCH'
            }
        }
        stage('Verify Branch') {
            steps {
                sh 'git checkout docker_branch'
                echo 'workspace is $WORKSPACE'
                echo '$GIT_BRANCH'
                
            }
        }


    }
}

