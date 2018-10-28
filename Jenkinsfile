pipeline {
  agent {
    label 'java-maven'
  }
  stages {
    stage('Buzz Build') {
      steps {
          echo 'Buzz Build'
      }
    }
    stage('Buzz Test') {
      parallel {
        stage('Testing A') {
          steps {
              echo 'Buzz Test A'
          }
        }
        stage('Testing B') {
          steps {
            echo 'Buzz Test B'
            sh '''sleep 10
            echo done.'''
          }
        }
      }
    }
  }
  environment {
    BUZZ_NAME = 'Worker Bee'
  }
}
