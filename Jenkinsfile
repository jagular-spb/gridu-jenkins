pipeline {
  agent any
  enviroment {
    HOSTNAME='Where we are?'
    }
  
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
	    enviroment { HOSTNAME=HOSTNAME0}
	    
	    echo "stg1:"+${HOSTNAME}
	}
    }

    stage('job2') {
	steps {
	    echo "stg2:"+${HOSTNAME}
	    echo "stg2 with env: ${env.HOSTNAME1}"
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