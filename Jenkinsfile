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
//    }

    post {
    success{
//    stage('job2') {
//	steps {
	    dockerNode(image: 'docker.io/jenkinsci/slave:latest') {
		echo "stg2:"+env.HOSTNAME0
	    }
//	}
//    }
    }
    }
    }

}

    post {
        always {
            echo 'I have finished'
            deleteDir() // clean up workspace
        }
        success {
            echo 'I succeeded!'
        }
        unstable {
            echo 'I am unstable :/'
        }
        failure {
            echo 'I failed :('
        }
        changed {
            echo 'Things are different...'
        }
    }    

    
	
  
  options {
    timestamps()
    newContainerPerStage()
  }
  triggers {
    pollSCM('H/15 * * * *')
  }
}