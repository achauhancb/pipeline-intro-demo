pipeline {
  agent {
   kubernetes {
     label 'java8-maven3-pod'
     yaml """
apiVersion: v1
kind: Pod
spec:
 containers:
 - name: maven3
   image: maven:3.3.9-jdk-8-alpine
   command: ['cat']
   tty: true
"""
   }
 }
  stages {
    stage('Buzz Build') {
      steps {
        container('maven3') {
          sh 'mvn -version'
        }
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
