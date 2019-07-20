pipeline {
  agent any
  stages {
    stage('Build-1') {
      parallel {
        stage('Build-1') {
          steps {
            sh 'mvn clean'
          }
        }
        stage('Build Gruyere') {
          steps {
            sh 'sudo make gruyere-start'
          }
        }
      }
    }
    stage('Test') {
      parallel {
        stage('Test') {
          steps {
            sh 'mvn test'
          }
        }
        stage('gauntlt-test') {
          steps {
            sh 'sudo gauntlt-docker ./attacks/xss/xss.attack'
          }
        }
      }
    }
    stage('Deploy') {
      steps {
        sh 'mvn package'
      }
    }
  }
}