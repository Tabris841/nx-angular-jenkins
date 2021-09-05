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
        sh 'npx nx run-many --target=test --all --codeCoverage'
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

    	stage('Sonarqube') {
			steps {
				sh "npm run sonar"
			}
		}
  }
}
