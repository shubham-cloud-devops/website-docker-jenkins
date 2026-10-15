
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/YOUR-USERNAME/YOUR-REPOSITORY.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'sudo docker build -t my-static-website .'
            }
        }

        stage('Deploy Container') {
            steps {
                sh '''
                    sudo docker rm -f my-website || true
                    sudo docker run -d \
                      --name my-website \
                      --restart unless-stopped \
                      -p 8080:80 \
                      my-static-website
                '''
            }
        }
    }
}

