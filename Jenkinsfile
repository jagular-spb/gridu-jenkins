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
              mail(subject: 'Result', body: 'env.HOSTNAME', from: 'Jenkins', to: 'root@loclahost')
            }

          }
        }
        stage('stg2') {
          steps {
            timestamps() {
              dockerNode(image: 'docker.io/jenkinsci/slave:latest') {
                echo 'stg2:'+env.HOSTNAME
              }

            }

            waitUntil() {
              echo 'env.HOSTNAME'
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