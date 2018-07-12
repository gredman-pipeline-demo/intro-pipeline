pipeline {
  agent {
    label 'jdk8'
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