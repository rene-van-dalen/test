pipeline {
  agent {
    docker {
      args '-p 8080:8080 -p 28015:28015 -p 29015:29015'
      image 'rethinkdb'
    }

  }
  stages {
    stage('Build') {
      steps {
        sh 'apt-get update'
      }
    }

  }
}