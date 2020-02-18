pipeline {
  agent none
  stages {
    stage('Build') {
      steps {
        git(url: 'https://github.com/rethinkdb/rethinkdb-dockerfiles', branch: 'jessie/2.3.6')
      }
    }

    stage('') {
      steps {
        echo 'test'
      }
    }

  }
}