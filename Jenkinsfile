pipeline {
  agent {
    docker {
      image 'rethinkdb'
      args '-p 8081:8080 -p 28015:28015 -p 29015:29015'
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