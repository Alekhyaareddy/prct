pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                git 'https://github.com/Alekhyaareddy/prct.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t myweb_image .'
            }
        }

        stage('Stop Old Container') {
            steps {
                bat 'docker stop myweb || exit 0'
                bat 'docker rm myweb || exit 0'
            }
        }

        stage('Run Container') {
            steps {
                bat 'docker run -d --name myweb -p 8085:80 myweb_image'
            }
        }
    }
}