pipeline {
  agent any

  
  stages {
    stage('job1') {
	steps {
	    dockerNode(image: 'docker.io/jenkinsci/slave:latest') {
                script {
        		env.HOSTNAME0 = sh(
                	script: "hostname",
            		returnStdout: true
            		).trim()
            	}
            	echo "stg1:"+env.HOSTNAME0
	    }
	    echo "stg1.1:"+env.HOSTNAME0
	}
    }

    stage('job2') {
	steps {
	    dockerNode(image: 'docker.io/jenkinsci/slave:latest') {
		echo "stg2:"+env.HOSTNAME0
	    }
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