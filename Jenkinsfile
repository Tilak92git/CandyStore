pipeline {
    agent any

    stages {
        stage('clone') {
            steps {
                checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/tilak92git/CandyStore.git']]) 
            }
        }
        stage('docker') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'doc-cred') {
                         sh 'docker build -t tilakpoludasu/candystore .'
                         sh 'docker push tilakpoludasu/candystore:latest'
                   }
               }
            }
        }
    }
}
