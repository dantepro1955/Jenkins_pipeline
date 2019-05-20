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
        script {
          status = sh(returnStatus: true, script: "return 0")
          if (status == 0) {
            echo 'Succeeded!'
            emailext(subject: 'Succeeded', body: 'Succeeded', to: 'overtherainbow_dg@yahoo.com')
          } else {
            echo "Failed"
            sh(returnStatus: true, script: "ps aux")
            emailext(subject: 'Failed', body: 'Failed', to: 'overtherainbow_dg@yahoo.com')
          }
          status = sh(returnStatus: true, script: "return 0")
        }
      }
    }
  }
}
