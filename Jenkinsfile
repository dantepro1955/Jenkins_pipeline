pipeline {
  agent any
  stages {
    stage('Step 1') {
      steps {
        sh 'ps aux'
        sh 'return 0'
        warnError(message: 'catch', catchInterruptions: true) {
          sh 'return 1'
        }

        sh 'return 0'
      }
    }
  }
}