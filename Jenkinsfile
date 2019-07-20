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
            sh 'make gruyere-start'
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
            sh 'gauntlt-docker ./attacks/xss/xss.attack'
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
