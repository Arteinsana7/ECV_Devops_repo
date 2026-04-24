pipeline {
  agent any

  options {
    disableConcurrentBuilds()
    parallelsAlwaysFailFast()
  }

  environment {
    IMAGE_NAME = 'ecv-devops-app'
  }

  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }

    stage('Install') {
      steps {
        sh 'npm ci'
      }
    }

    stage('Lint') {
      steps {
        sh 'npm run lint'
      }
    }

    stage('Tests') {
      steps {
        sh 'npm run test:coverage'
      }
    }

    stage('Docker Build') {
      steps {
        sh 'docker build -t ${IMAGE_NAME}:${BUILD_NUMBER} .'
        sh 'docker tag ${IMAGE_NAME}:${BUILD_NUMBER} ${IMAGE_NAME}:latest'
      }
    }

    stage('Deploy') {
      steps {
        sh 'docker stop ${IMAGE_NAME} || true'
        sh 'docker rm ${IMAGE_NAME} || true'
        sh 'docker run -d -p 3000:3000 --name ${IMAGE_NAME} ${IMAGE_NAME}:latest'
      }
    }
  }

  post {
    success {
      echo 'Pipeline reussi ✅'
    }
    failure {
      echo 'Pipeline en echec ❌'
    }
  }
}