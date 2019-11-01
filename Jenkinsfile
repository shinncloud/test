pipeline {
agent any

  stages {
    stage('Capture Output') {
      steps {
        script {
          myShOutput = sh(returnStdout: true, script: 'echo "stdout from sh step"')
        }
      }

      post {
        always {
          script {
          if (env.CHANGE_ID) {
              githubPRComment(comment: githubPRMessage('My step output\n ${myShOutput}'))
            }
          }
        }
      }
    }
  }
}
