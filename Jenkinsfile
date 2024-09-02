pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'docker build -t nodejs-random-color:ver-${BUILD_ID} .'
            }
        }
        stage('Upload image to ECR') {
            steps {
                sh 'aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 220299120849.dkr.ecr.us-east-1.amazonaws.com'
                sh 'docker tag nodejs-random-color:ver-${BUILD_ID} 220299120849.dkr.ecr.us-east-1.amazonaws.com/nodejs-random-color:ver-${BUILD_ID}'
                sh 'docker push 220299120849.dkr.ecr.us-east-1.amazonaws.com/nodejs-random-color:ver-${BUILD_ID}'
            }
        }
    }
}
