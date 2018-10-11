
pipeline {
    agent any
    options {
	timestamps()
    }

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

pipeline {
    agent any
    options {
	timestamps()
    }

    stages {  
	stage('stg2') {
	    steps{
		echo env.HOSTNAME
	    }
	}

    
    }
}
