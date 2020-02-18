pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        git 'https://github.com/rethinkdb/rethinkdb-dockerfiles'
        sh 'docker compose .'
      }
    }

  }
}