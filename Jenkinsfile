node {
  withEnv(["HOME=${workspace}"]) {
    docker.image('node:latest').inside('--tmpfs /.config') {
      stage("Prepare") {
        checkout scm
        sh 'yarn install'
      }

      stage("Test") {
        sh 'yarn nx affected --target=test --base=origin/main'
      }

      stage("Lint") {
        sh 'yarn nx affected --target=lint --base=origin/main'
      }

      stage("Build") {
        sh 'yarn nx affected --target=build --base=origin/main --prod'
      }
    }
  }
}
