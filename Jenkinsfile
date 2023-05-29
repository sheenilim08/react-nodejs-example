pipeline {
  agent any
  stages {
    stage('deploy server to EC2') {
      steps {
        script {
          withCredentials([usernamePassword(credentialsId: 'docker-hub-credentials.', passwordVariable: 'PASS', usernameVariable: 'USER')]) {
            sh "echo $PASS | docker login -u $USER --password-stdin"
          }
          
          def dockerCmd = "docker run -d -p 8080:80 sheenismhaellim/itfellas:demo-app-1.0"
          sshagent(['ec2-instance-dockerserver']) {
            sh "ssh -o StrictHostKeyChecking=no ec2-user@13.210.196.30 ${dockerCmd}"
          }
        }
      }
    }
  }
}
