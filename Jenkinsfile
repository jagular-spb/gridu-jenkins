pipeline {
    agent any
    stages {  
	stage('stg1') {
	    steps {
	    echo 'wtf'
		dockerNode(image: 'docker.io/jenkinsci/slave:latest') {
            	    script {
			env.HOSTNAME = sh(
                    	    script: "hostname",
                    	    returnStdout: true
                	).trim()
            	    }
		}
	    }
	}
    }
  environment {
    user = 'Jenkins'
  }
}