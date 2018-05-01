pipeline {
  agent {
    label 'jdk9'
  }
  stages {
    stage('say hello') {
      steps {
        echo "Hello ${MY_NAME}!"
        sh 'java -version'
      }
    }
  }
  environment {
    My_Name = 'Sri'
  }
}