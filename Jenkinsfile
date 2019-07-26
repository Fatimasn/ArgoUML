#!groovy

if (env.GERRIT_API_URL == null) {
  this.gerritComment = { dict -> }
  this.gerritReview = { dict -> }
}

pipeline {
  agent {
      docker { image 'java:oracle-java8' }
  }
  stages {
    stage('checkout') {
      steps {
        checkout scm
      }
    }
    stage('compile') {
      steps {
        sh 'mvn -B compile'
      }
    }
    stage('test') {
      steps {
        sh 'mvn -B test'
      }
    }
  }
}

// gerritReview labels: [:], message: "Build started ${env.BUILD_URL} doing nothing."

