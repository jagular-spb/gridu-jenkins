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
	stage('stg2') {
	    steps{
		echo env.HOSTNAME
	    }
	}
	
    }
  environment {
    user = 'Jenkins'
  }
}