pipeline {
    agent any
    stages {
        stage('Verify Branch') {
            steps {
                echo '$GIT_BRANCH'
            }
        }
        stage('Verify Workspace') {
            steps {
                echo '$WORKSPACE'
            }
        }

    }
}
