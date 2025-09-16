pipeline {
    agent any
    stages {
        stage("Build") {
            steps {
                sh 'docker build -t image1 .'
            }
        }
        stage("Tag") {
            steps {
                sh 'docker tag image1 narendra772/paytm:bank'
            }
        }
        stage("Push") {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker') {
                        sh 'docker push narendra772/paytm:bank'
                    }
                }
            }
        }
        stage("Deploy") {
            steps {
                script {
                    sh '''
                        docker rm -f bank || true
                        docker run -itd --name bank -p 4455:80 narendra772/paytm:bank
                    '''
                }
            }
        }
    }
}
