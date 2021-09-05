pipeline {
  agent {
    docker { image 'node:latest' }
  }
  stages {
    stage('Install') {
      steps {
        sh 'yarn install'
      }
    }

    stage('Test') {
      steps {
        sh 'yarn nx affected --target=test --base=origin/main --parallel'
      }
    }

    stage('Lint') {
      steps {
        sh 'yarn nx affected --target=lint --base=origin/main --parallel'
      }
    }

    stage('Build') {
      steps {
        sh 'yarn nx affected --target=build --base=origin/main --prod --parallel'
      }
    }
  }
}
