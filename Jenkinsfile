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
