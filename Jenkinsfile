pipeline {
 
  agent {
        docker.withDockerServer('tcp://127.0.0.1:2376')
        {
            docker.image('docker.io/jenkinsci/slave:latest')
        }
    }
    
  stages {
    stage('stg1') {
      steps {
        echo 'wtf'
        isUnix()
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