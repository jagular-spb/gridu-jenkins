
pipeline {
    agent any
    triggers{ cron('H/15 * * * *') }
    options {
	timestamps()
	newContainerPerStage()
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
            	    echo env.HOSTNAME
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
	newContainerPerStage()
    }

    stages {  
	stage('stg2') {
	    steps{
		echo 'env.HOSTNAME'
	    }
	}

    
    }
}
