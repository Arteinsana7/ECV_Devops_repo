pipeline {
  agent any

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
        sh 'docker build -t ecv-devops-app .'
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