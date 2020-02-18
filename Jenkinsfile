pipeline {
  agent {
    dockerfile {
      filename 'Dockerfile'
    }

  }
  stages {
    stage('Build') {
      steps {
        git(url: 'https://github.com/rethinkdb/rethinkdb-dockerfiles', branch: 'jessie/2.3.6')
        sh 'docker compose .'
      }
    }

  }
}