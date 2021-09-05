pipeline {

  agent {
    docker { image 'node:latest' }
  }

  stages {
    stage('Prepare') {
      checkout scm
      sh 'yarn install'
    }

    stage("Test") {
      sh 'yarn nx affected --target=test --base=origin/main --parallel'
    }

    stage("Lint") {
      sh 'yarn nx affected --target=lint --base=origin/main --parallel'
    }

    stage("Build") {
      sh 'yarn nx affected --target=build --base=origin/main --prod --parallel'
    }
  }
}
