pipeline {
  agent {
    docker { image 'node:12' }
  }
  stages {
    stage('Install') {
      steps {
        sh 'npm install'
      }
    }

    stage('Test') {
      steps {
        sh 'npx nx affected --target=test --base=origin/main --parallel'
      }
    }

    stage('Lint') {
      steps {
        sh 'npx nx affected --target=lint --base=origin/main --parallel'
      }
    }

    stage('Build') {
      steps {
        sh 'npx nx affected --target=build --base=origin/main --prod --parallel'
      }
    }
  }
}
