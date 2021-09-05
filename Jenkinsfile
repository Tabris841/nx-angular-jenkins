pipeline {
  agent {
    docker { image 'node:latest' }
  }
  stages {
    stage('Install') {
      steps {
        sh 'npm install'
      }
    }

    stage('Test') {
      steps {
        sh 'npx nx run-many --target=test --all'
      }
    }

    stage('Lint') {
      steps {
        sh 'npx nx run-many --target=lint --all'
      }
    }

    stage('Build') {
      steps {
        sh 'npx nx run-many --target=build --all --prod'
      }
    }
  }
}
