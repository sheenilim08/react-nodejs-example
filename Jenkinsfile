pipeline {
  agent any
  stages {
    stage('deploy server to EC2') {
      script {
        sshagent(['ec2-docker-server']) {
        // some block
        }
      }
    }
  }
}
