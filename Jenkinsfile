pipeline {
  agent {
    label 'jdk8'
  }
  stages {
    stage('Say hello') {
      steps {
        echo "Hello ${params.Name}!"
        echo "${TEST_USER_USR}"
        echo "${TEST_USER_PSW}"
        sh 'java -version'
      }
    }
    stage('Testing') {
        parallel {
          stage('Java 8') {
            agent { label 'jdk9' }
            steps {
              container('maven8') {
                sh 'mvn -v'
              }
            }
          }
          stage('Java 9') {
            agent { label 'jdk8' }
            steps {
              container('maven9') {
                sh 'mvn -v'
              }
            }
          }
        }
      }
    stage('Checkpoint') {
      steps {
        checkpoint 'Checkpoint'
      }
    }
    stage('Deploy') {
      agent {
        label 'jdk9'
      }
      steps {
        echo 'Deploying....'
      }
    }
  }
  environment {
    MY_NAME = 'Frank'
    TEST_USER = credentials('test-user')
  }
  post {
    aborted {
      echo 'Why didn\'t you push my button?'

    }

  }
  parameters {
    string(name: 'Name', defaultValue: 'whoever you are', description: 'Who should I say hi to?')
  }
}
