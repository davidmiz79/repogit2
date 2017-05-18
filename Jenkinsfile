pipeline {
  agent { label 'master' }
    stages {
      stage('Deploy staging') {
        steps {
          echo 'Hello World'
        }
      }
      stage ('Ask for input') {
        steps {
          input "Continue?"
        }
      }
      stage('Deploy to production') {
        steps {
          echo 'Deploy to production'
        }
      }
    }
  post {
    failure {
      mail to: 'davidmi@meta4.com',
      subject: "Failed Pipeline: ${currentBuild.fullDisplayName}",
      body: "Something is wrong with ${env.BUILD_URL}"
    }
    success {
      mail to: 'davidmi@meta4.com',
      subject: "Success Pipeline: ${currentBuild.fullDisplayName}",
      body: "Url: ${env.BUILD_URL}"
    }
  }
}
