pipeline {
  agent {
    docker { image 'node:latest' }
  }
  stages {
    stage('Install') {
      steps {
        sh 'npm ci'
      }
    }

    stage('Test') {
      steps {
        sh 'nx affected --target=test --base=origin/main --parallel'
      }
    }

    stage('Lint') {
      steps {
        sh 'nx affected --target=lint --base=origin/main --parallel'
      }
    }

    stage('Build') {
      steps {
        sh 'nx affected --target=build --base=origin/main --prod --parallel'
      }
    }
  }
}
