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
        isUnix()
        sh 'returnStdout: true, script: \'hostname\''
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