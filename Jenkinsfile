pipeline {
    agent any
    environment {
        DOCKER_HUB_CREDENTIALS = credentials('docker-hub-credentials-id')
        IMAGE_NAME = 'amalsthayyil/podinfo'
        TAG = "${env.BUILD_NUMBER}"
    }
    stages {
        stage('Build & Push Image') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'docker-hub-credentials-id') {
                        def customImage = docker.build("${IMAGE_NAME}:${TAG}")
                        customImage.push()
                        customImage.push('latest')
                    }
                }
            }
        }
    }
}