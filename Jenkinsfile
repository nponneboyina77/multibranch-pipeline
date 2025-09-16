pipeline {
    agent any
    stages {
        stage ("Build") {
            steps {
                sh 'docker build -t image3 .'
            }
        }
        stage ("tag") {
               steps {
                   sh "docker tag image3 narendra772/paytm:train"
               }
        }
        stage('push') {
            steps {
                script {
                withDockerRegistry(credentialsId: 'docker') {
                 sh 'docker push narendra772/paytm:tain'
                }
             }
         }
      }
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name train -p 9999:80 shaikmustafa/abinay:train'
            }
        }
    }
}
