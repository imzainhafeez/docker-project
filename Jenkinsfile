pipeline {
  agent any

  stages {
      stage('Checkout') {
          steps {
              // Checkout your source code from your GitHub repository
              git url: 'https://github.com/imzainazm/docker-project.git', branch: 'develop'
          }
      }

      stage('Build Docker Image') {
          steps {
              // Build Docker image with sudo privileges
              script {
                  sh 'docker build -t imzainazm/nodeapp:latest .'
              }
          }
      }

      stage('Push Docker Image to Docker Hub') {
          steps {
              // Push Docker image to Docker Hub
              script {
                  docker.withRegistry('https://index.docker.io/v1/', 'ab92c762-d9b2-4961-8584-61e55498a467') {
                      docker.image('imzainazm/nodeapp:latest').push()
                  }
              }
          }
      }
  }
}
