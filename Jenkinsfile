pipeline {
  agent {
    docker {
      image 'docker.io/jenkinsci/slave:latest'
    }

  }
  stages {
    stage('stg1') {
      steps {
        echo 'wtf'
      }
    }
  }
  environment {
    user = 'Jenkins'
  }
}