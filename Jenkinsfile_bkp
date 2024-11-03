def repoName() {
  return GIT_URL.tokenize('/.')[-2]
}

pipeline {
    agent any

    environment {
      REPO_NAME = repoName()
      REGISTRY_CRED = credentials('registry-cred')
    }
      
    stages {
        stage('docker build') {
            steps {
                echo 'Hello from multiple-branch'
                sh 'docker build -t ${REGISTRY_CRED_USR}/${REPO_NAME}:${BUILD_NUMBER} .'
            }
        }

        stage('docker push') {
            steps {
                echo 'logging in to the container registry'
                sh 'docker login -u ${REGISTRY_CRED_USR} -p ${REGISTRY_CRED_PSW}'
                sh 'docker push ${REGISTRY_CRED_USR}/${REPO_NAME}:${BUILD_NUMBER}'
            }
        }

    }
}

