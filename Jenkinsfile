pipeline {
  agent any
  stages {
    stage('stg1') {
      parallel {
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

              echo "stg1:"+env.HOSTNAME
            }

          }
        }
        stage('stg2') {
          steps {
            timestamps() {
              echo 'ok'
            }

          }
        }
      }
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