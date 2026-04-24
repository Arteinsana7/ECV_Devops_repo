
pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }

    stage('Install') {
      agent {
        docker {
          image 'node:18-alpine'
          reuseNode true
        }
      }
      steps {
        sh 'npm ci'
      }
    }

    stage('Lint') {
      agent {
        docker {
          image 'node:18-alpine'
          reuseNode true
        }
      }
      steps {
        sh 'npm run lint'
      }
    }

    stage('Tests') {
      agent {
        docker {
          image 'node:18-alpine'
          reuseNode true
        }
      }
      steps {
        sh 'npm run test:coverage'
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
