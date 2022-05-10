pipeline{
  agent any
    stages{
    stage('maven build') {
        steps{
          sh "maven clean package"
        }
      }
      stage('deploy to tomcat') {
        steps{
          echo"deploying tomcat in jenkins"
        }
      }
    }
  post{
    success{
      archiveArtifacts artifacts: 'target/*.war'
      cleanWs()
    }
  }
} 
