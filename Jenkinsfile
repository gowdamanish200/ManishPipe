pipeline {
  agent any
  stages {
    stage('Build') {
      parallel {
        stage('Build') {
          steps {
            sh '''sh
pwd
cat
cd
date'''
            sleep 15
            retry(count: 3) {
              echo 'print manish'
            }

          }
        }

        stage('Pre-Build ') {
          steps {
            bat(script: 'java', returnStatus: true)
            cleanWs(cleanWhenAborted: true, cleanWhenFailure: true, cleanWhenNotBuilt: true, notFailBuild: true, skipWhenFailed: true)
          }
        }

        stage('Post-Build') {
          steps {
            timeout(time: 30, activity: true)
            warnError(message: 'error should be resolved', catchInterruptions: true) {
              sh '''sh 
date
'''
            }

          }
        }

      }
    }

    stage('Test') {
      steps {
        sleep 15
      }
    }

    stage('Pre-prod') {
      steps {
        sh '''sh 
pwd
date'''
      }
    }

    stage('Post-prod') {
      steps {
        echo 'i am manish'
      }
    }

  }
}