pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        git 'https://github.com/rethinkdb/rethinkdb-dockerfiles'
      }
    }

    stage('Build to ICR') {
      steps {
        sh '''#!/bin/bash



# uncomment to debug the script
# set -x
# copy the script below into your app code repo (e.g. ./scripts/build_image.sh) and \'source\' it from your pipeline job
#    source ./scripts/build_image.sh
# alternatively, you can source it from online script:
#    source <(curl -sSL "https://raw.githubusercontent.com/open-toolchain/commons/master/scripts/build_image.sh")
# ------------------
# source: https://raw.githubusercontent.com/open-toolchain/commons/master/scripts/build_image.sh
# This script does build a Docker image into IBM Container Service private image registry.
# Minting image tag using format: BUILD_NUMBER-BRANCH-COMMIT_ID-TIMESTAMP
# Also copies information into a build.properties file, so they can be reused later on by other scripts (e.g. image url, chart name, ...)
source ~/build_image.sh
'''
      }
    }

    stage('Check vulscan') {
      steps {
        load 'build.properties'
        sh '''#!/bin/bash
# uncomment to debug the script
# set -x
# copy the script below into your app code repo (e.g. ./scripts/check_vulnerabilities.sh) and \'source\' it from your pipeline job
#    source ./scripts/check_vulnerabilities.sh
# alternatively, you can source it from online script:
#    source <(curl -sSL "https://raw.githubusercontent.com/open-toolchain/commons/master/scripts/check_vulnerabilities.sh")
# ------------------
# source: https://raw.githubusercontent.com/open-toolchain/commons/master/scripts/check_vulnerabilities.sh
# Check for vulnerabilities of built image using Vulnerability Advisor
source <(curl -sSL "https://raw.githubusercontent.com/open-toolchain/commons/master/scripts/check_vulnerabilities.sh")
'''
      }
    }

  }
  environment {
    REGISTRY_URL = 'de.icr.io'
    IMAGE_NAME = 'rethink-rvd-tst4'
    REGISTRY_NAMESPACE = 'r2r-platform'
    DOCKER_ROOT = 'buster/2.4.0'
    ARCHIVE_DIR = '.'
    IMAGE_TAG = 'latest'
  }
}