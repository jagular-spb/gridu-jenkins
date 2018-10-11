pipeline {
  agent any
  stages {
    stage('job1') {
	steps {
	    dockerNode(image: 'docker.io/jenkinsci/slave:latest') {
                script {
        		HOSTNAME0 = sh(
                	script: "hostname",
            		returnStdout: true
            		).trim()
            	}
            	echo "stg1:"+HOSTNAME0
	    }
	    echo "stg1:"+HOSTNAME              
	}
    }
}    

    
	
  environment {
    HOSTNAME0 = 'Jenkins'
  }
  
  options {
    timestamps()
    newContainerPerStage()
  }
  triggers {
    cron('H/15 * * * *')
  }
}