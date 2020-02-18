pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        git 'https://github.com/rethinkdb/rethinkdb-dockerfiles'
        sh 'docker build jessie/2.3.6 '
      }
    }

  }
}