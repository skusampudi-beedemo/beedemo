pipeline {
  agent {
    label 'jdk9'
  }
  stages {
    stage('say hello') {
      steps {
        echo "Hello ${params.Name}!"
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
  }
  environment {
    My_Name = 'Sri'
    TEST_USER = credentials('test-user')
  }
  parameters {
    string(name: 'Name', defaultValue: 'whoever you are', description: 'Who should I say hi to?')
  }
    post {
    aborted {
      echo 'Why didn\'t you push my button?'
    }
  }
}
