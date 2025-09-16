pipeline {
    agent any
    stages {
        stage ("Build") {
            steps {
                sh 'docker build -t shaikmustafa/abinay:bus .'
            }
        }
        stage ("tag") {
               steps {
                   sh "docker tag image2 narendra772/paytm:bus"
               }
        }
        stage('push') {
            steps {
                script {
                withDockerRegistry(credentialsId: 'docker') {
                 sh 'docker push narendra772/paytm:bus '
                }
             }
         }
      }
        
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name bus -p 8888:80 shaikmustafa/abinay:bus'
            }
        }
    }
}
