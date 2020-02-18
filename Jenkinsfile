pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        git 'https://github.com/rethinkdb/rethinkdb-dockerfiles'
        sh 'docker build buster/2.4.0'
      }
    }

  }
}