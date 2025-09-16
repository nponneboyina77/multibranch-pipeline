pipeline {
    agent any
    stages {
        stage("Build") {
            steps {
                sh 'docker build -t image3 .'
            }
        }
        stage("Tag") {
            steps {
                sh 'docker tag image3 narendra772/paytm:train'
            }
        }
        stage("Push") {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker') {
                        sh 'docker push narendra772/paytm:train'
                    }
                }
            }
        }
        stage("Deploy") {
            steps {
                script {
                    sh '''
                        docker rm -f train || true
                        docker run -itd --name train -p 4455:80 narendra772/paytm:train
                    '''
                }
            }
        }
    }
}
