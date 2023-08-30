pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                sh 'docker build -t sample -f Dockerfile .'
                sh 'aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 108177350548.dkr.ecr.us-east-1.amazonaws.com'
                sh 'docker tag sample:latest 108177350548.dkr.ecr.us-east-1.amazonaws.com/nginxapp:$BUILD_NUMBER'
                sh 'docker push 108177350548.dkr.ecr.us-east-1.amazonaws.com/nginxapp:$BUILD_NUMBER'
            }
        }
    }
}
