pipeline {
 
  agent {
        docker {
	    image "docker.io/jenkinsci/slave:latest"
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