pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
               aws ecr get-login-password --region eu-west-1 | docker login --username AWS --password-stdin 933060838752.dkr.ecr.eu-west-1.amazonaws.com
               docker build -t roberta_saeedha .
               docker tag roberta_saeedha:latest 933060838752.dkr.ecr.eu-west-1.amazonaws.com/roberta_saeedha:latest
               docker push 933060838752.dkr.ecr.eu-west-1.amazonaws.com/roberta_saeedha:latest

            }
        }
    }
}