pipeline {
  agent {
    docker {
      image 'node:lts-bullseye-slim'
      args '-p 3000:3000'
    }

  }
  stages {
    stage('build') {
      steps {
        sh 'npm install'
      }
    }

    stage('test') {
      environment {
        CI = 'true'
      }
      steps {
        sh 'npm test'
      }
    }

    stage('deliver') {
      steps {
        sh 'npm start'
        input ' Finished using the web site? (Select "Proceed" to continue)'
        sh '/jenkins/scripts/kill.sh'
      }
    }

  }
}