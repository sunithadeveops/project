pipeline {
  agent any
    stages {
      stage('Maven Build') {
        steps {
          sh 'mvn clean package'
      }
    }
     stage('Deploy to Tomcat') {
      steps {
        sshagent(['tomcat']) {
            // Copy war file to tomcat server
            sh 'scp -o StrictHostKeyChecking=no target/*.war ec2-user@3.109.157.105:/opt/tomcat8/webapps/app.war'
            // stopt tomcat
            sh "ssh ec2-user@3.109.157.105 /opt/tomcat8/bin/shutdown.sh"
            // start tomcat
            sh "ssh ec2-user@3.109.157.105 /opt/tomcat8/bin/startup.sh"
        }
      }
    }
  }
  post {
    success {
      archiveArtifacts artifacts: 'target/*.war'
      cleanWs()
    }
  }
}

