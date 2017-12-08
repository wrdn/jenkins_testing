pipeline {
  agent any
  stages {
    stage('Build') {
      parallel {
        stage('a') {
          steps {
            echo 'This is branch a'
          }
        }
        stage('b') {
          steps {
            echo 'This is branch b'
          }
        }
        stage('c') {
          steps {
            writeFile(file: 'file', text: 'some text..')
            sleep 5
          }
        }
      }
    }
    stage('Test') {
      steps {
        echo 'Testing..'
      }
    }
    stage('Deploy') {
      steps {
        echo 'Deploying....'
      }
    }
  }
}