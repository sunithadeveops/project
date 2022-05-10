pipeline{
  agent any{
    stages{
      stage('maven demo') {
        steps{
          sh 'echo jenkins demo'
        }
      }
    }
    post {
  success {
      echo "this is success block"
  }
  failure {
      echo "this is failure block"
  }
}
  }
