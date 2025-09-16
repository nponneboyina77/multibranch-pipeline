pipeline {
    agent any
    stages {
        stage("Build") {
            steps {
                sh 'docker build -t image2 .'
            }
        }
        stage("Tag") {
            steps {
                sh 'docker tag image2 narendra772/paytm:bus'
            }
        }
        stage("Push") {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker') {
                        sh 'docker push narendra772/paytm:bus'
                    }
                }
            }
        }
        stage("Deploy") {
            steps {
                script {
                    sh '''
                        docker rm -f bus || true
                        docker run -itd --name bank -p 4455:80 narendra772/paytm:bus
                    '''
                }
            }
        }
    }
}
