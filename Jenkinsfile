pipeline {
  agent any
  stages {
    stage('stg1') {
      steps {
        echo 'wtf'
        isUnix()
        sh 'hostname'
        dockerNode(image: 'docker.io/jenkinsci/slave:latest') {
          sh 'hostname'
        }

      }
    }
  }
  environment {
    user = 'Jenkins'
  }
}