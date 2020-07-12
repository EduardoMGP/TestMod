pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        sh 'Running build #${env.BUILD_ID} on ${env.JENKINS_URL}'
        sh 'checkout scm'
      }
    }

    stage('Build') {
      steps {
        sh 'rm -rf build/libs/'
        sh 'rm -rf build/repo/'
        sh 'chmod +x gradlew'
        sh './gradlew build uploadArchives --no-daemon'
      }
    }

  }
  environment {
    MAVEN_URL = '/var/www/mvn.romvoid.dev/public'
  }
}