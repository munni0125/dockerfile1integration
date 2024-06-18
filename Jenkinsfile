pipeline {
    agent any  // Adjust if you need a specific agent (e.g., label)
    environment {
        DOCKERHUB_CREDENTIALS = credentials('tokendocker')
    }
     
    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', // Replace with your branch name
                    url: 'https://github.com/munni0125/dockerfile1integration.git' // Replace with your Git repository URL
            }
        }
        stage('Build Docker Image') {
            steps {
                bat 'docker build -t mounikadockerimage .' // Replace with your image name
            }
        }
        stage('Run Tests (Optional)') {
            steps {
                script {
                    // Customize testing commands based on your framework and container environment
                    bat 'docker run -d --name cont6 -p 8088:80 mounikadockerimage'
                }
            }
        }
        stage('Deploy Image (Optional)') {
            steps {
                bat 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('push image') {
            steps {
                bat 'docker tag mounikadockerimage MounikaMunniAloor/munnirepo44'
                bat 'docker push MounikaMunniAloor/munnirepo44'
            }
        }
    }


}
