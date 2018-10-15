pipeline {
  agent any
  stages {
    stage('job1') {
      post {
        success {
          dockerNode(image: 'docker.io/mzagar/jenkins-slave-jdk-maven-git:latest') {
            echo "stg2:"+env.HOSTNAME0
          }


        }

      }
      steps {
        dockerNode(image: 'docker.io/mzagar/jenkins-slave-jdk-maven-git:latest') {
          script {
            env.HOSTNAME0 = sh(
              script: "hostname",
              returnStdout: true
            ).trim()
          }

          echo "stg1:"+env.HOSTNAME0
          checkout([$class: 'GitSCM', branches: [[name: "${env.BRANCH}"]], doGenerateSubmoduleConfigurations: false, extensions: [[$class: 'CleanBeforeCheckout']], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/jagular-spb/gridu-mvn.git']]])
	  sh '''
              mkdir -p ~/.m2 && \
              echo "<settingsSecurity><master>{ZZmYMzlo6CsHo0ydXp+Isvm4K56700ioJcPnm2s2FcE=}</master></settingsSecurity>" > ~/.m2/settings-security.xml && \
              echo "<settings><mirrors><mirror><id>nexus</id><mirrorOf>*</mirrorOf><url>http://172.17.0.1:8081/repository/maven-public/</url></mirror></mirrors><profiles><profile><id>nexus</id><repositories><repository><id>central</id><url>http://central</url><releases><enabled>true</enabled></releases><snapshots><enabled>true</enabled></snapshots></repository></repositories><pluginRepositories><pluginRepository><id>central</id><url>http://central</url><releases><enabled>true</enabled></releases><snapshots><enabled>true</enabled></snapshots></pluginRepository></pluginRepositories></profile></profiles><activeProfiles><activeProfile>nexus</activeProfile></activeProfiles><servers><server><id>git.7579433</id><username>admin</username><password>{W5oxlv3TImkHJ9yURWZSF1SAspr/beBOTeHN8Dd+JDs=}</password></server></servers></settings>" > ~/.m2/settings.xml
          '''
          sh '''
          mvn -f main-app/pom.xml clean deploy
          '''
	 

        }
        echo "stg1.1:"+env.HOSTNAME0
      }
    }
  }
  environment {
    BRANCH = '*/nexus'
  }
  post {
    always {
      echo 'I have finished'
      deleteDir()

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