pipeline {
  agent any

  stages {
    stage('job1') {
	stages {
	stage('stg1')
	    steps {
        	echo 'wtf'
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
	 post {
	    success {
    		// One or more steps need to be included within each condition's block.
    		stages {
    		    stage ('stg2') {


          steps {
            timestamps() {
              dockerNode(image: 'docker.io/jenkinsci/slave:latest') {
                echo 'stg2:'+env.HOSTNAME
              }

            }

    		    
    			}
    		    
    		    }
		}
	    }
	}          
        }
        
        


  }
  
 post {
    success {
      // One or more steps need to be included within each condition's block.
      echo '0'
    }
  }  
  environment {
    user = 'Jenkins'
  }
  options {
    timestamps()
    newContainerPerStage()
  }
  triggers {
    cron('H/15 * * * *')
  }
}