pipeline {
  agent {
    label 'jdk9'
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