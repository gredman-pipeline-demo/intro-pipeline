pipeline {
  agent {
    label 'jdk9'
  }
  stages {
    stage('say hello') {
      steps {
        echo 'hello world'
        sh 'java -version'
      }
    }
  }
}