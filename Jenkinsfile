pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        git 'https://github.com/rethinkdb/rethinkdb-dockerfiles'
        sh '''#!/bin/bash



# uncomment to debug the script
# set -x
# copy the script below into your app code repo (e.g. ./scripts/build_image.sh) and \'source\' it from your pipeline job
#    source ./scripts/build_image.sh
# alternatively, you can source it from online script:
#    source <(curl -sSL "https://raw.githubusercontent.com/open-toolchain/commons/master/scripts/build_image.sh")
# ------------------
# source: https://raw.githubusercontent.com/open-toolchain/commons/master/scripts/build_image.sh
DOCKER_ROOT=4.2
# This script does build a Docker image into IBM Container Service private image registry.
# Minting image tag using format: BUILD_NUMBER-BRANCH-COMMIT_ID-TIMESTAMP
# Also copies information into a build.properties file, so they can be reused later on by other scripts (e.g. image url, chart name, ...)
source <(curl -sSL "https://raw.githubusercontent.com/open-toolchain/commons/master/scripts/build_image.sh")
'''
        sh 'docker build buster/2.4.0'
      }
    }

  }
  environment {
    REGISTRY_URL = 'de.icr.io'
    IMAGE_NAME = 'r2r-platform/rethink-rvd-tst4'
  }
}