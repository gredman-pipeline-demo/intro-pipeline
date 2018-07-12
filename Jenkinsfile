pipeline {
  agent {
    label 'jdk8'
  }
  stages {
    stage('say hello') {
      steps {
        echo "hello ${params.Name}"
        echo "${TEST_USER_USR}"
        echo "${TEST_USER_PSW}"
        sh 'java -version'
      }
    }
    stage('Testing') {
      failFast true
      parallel {
        stage('Java 8') {
          agent { label 'jdk8' }
          steps {
            sh 'java -version'
            sleep time: 10, unit: 'SECONDS'
          }
        }
        stage('Java 9') {
          agent { label 'jdk9' }
          steps {
            sh 'java -version'
            sleep time: 20, unit: 'SECONDS'
          }
        }
      }
    }
    stage('Checkpoint') {
      agent none
      steps {
        checkpoint 'Checkpoint'
      }
    }
  }
  environment {
    MY_NAME = 'gareth'
    TEST_USER = credentials('test-user')
  }
  parameters {
    string(name: 'Name', defaultValue: 'stranger', description: 'To whom shall I say hello?')
  }
  post {
    aborted {
      echo "why did you not press da button?"
    }
  }
}
