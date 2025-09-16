pipeline {
    agent any
    stages {
        stage ("Build") {
            steps {
                sh 'docker build -t image1 .'
            }
        }
        stage ("tag") {
               steps {
                   sh "docker tag image1 narendra772/paytm:bank"
               }
        }
        stage('push') {
            steps {
                script {
                withDockerRegistry(credentialsId: 'docker') {
                 sh 'docker push narendra772/paytm:bank'
                }
             }
         }
      }
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name bank2 -p 4455:80 shaikmustafa/abinay:bank'
            }
        }
    }
}
