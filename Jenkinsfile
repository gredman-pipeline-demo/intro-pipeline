pipeline {
  agent {
    label 'jdk8'
  }
  stages {
    stage('say hello') {
      steps {
        echo "hello ${MY_NAME}"
        sh 'java -version'
      }
    }
  }
  environment {
    MY_NAME = 'gareth'
  }
}