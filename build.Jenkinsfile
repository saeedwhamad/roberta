pipeline {
    agent any
    enviroment{
    aws_url = '933060838752.dkr.ecr.eu-west-1.amazonaws.com'
    repo_name = 'roberta_saeedha'
    }

    stages {
      stage('Build') {
            steps {
             sh  'aws ecr get-login-password --region eu-west-1 | docker login --username AWS --password-stdin $aws_url'
              sh 'docker build -t roberta_saeedha .'
               sh 'docker tag roberta_saeedha:latest $aws_url/$repo_name:$BUILD_NUMBER '
              sh 'docker push $aws_url/$repo_name:$BUILD_NUMBER'

            }
        }
    }
    stage('Trigger Deploy') {
        steps {
            build job: '<deploy-job-name>', wait: false, parameters: [
                string(name: 'ROBERTA_IMAGE_URL', value: "<full-url-to-docker-image>")
            ]
        }
}
}