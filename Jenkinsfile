node {
  withEnv(["HOME=${workspace}"]) {
    docker.image('node:latest').inside('--tmpfs /.config') {
      stage("Prepare") {
        checkout scm
        sh 'npm ci'
      }

      stage("Test") {
        sh 'nx affected --target=test --base=origin/main --parallel'
      }

      stage("Lint") {
        sh 'nx affected --target=lint --base=origin/main --parallel'
      }

      stage("Build") {
        sh 'nx affected --target=build --base=origin/main --prod --parallel'
      }
    }
  }
}
