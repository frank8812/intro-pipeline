pipeline {
  agent {
    label 'jdk8'
  }
  stages {
    stage('Say hello') {
      steps {
        echo 'Hello World!'
        sh 'java -version'
      }
    }
  }
}