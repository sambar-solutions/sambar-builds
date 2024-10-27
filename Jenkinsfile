pipeline {
    agent any

    stages {
        stage('print git url') {
            steps {
                sh 'echo ${GIT_URL}'
            }
        }
        stage('print build number') {
            steps {
                echo '$BUILD_NUMBER'
            }
        }
    }
}
