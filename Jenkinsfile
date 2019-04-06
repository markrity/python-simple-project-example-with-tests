pipeline {
  agent { docker { image 'python:3.7.2' } }
  stages {
    stage('Git'){
        steps{
            checkout scm
        }
    }
    stage('build') {
      steps {
        sh 'pip install --no-cache-dir -r requirements.txt'
      }
    }
    stage('Run Flask'){
          steps{
               sh "python app.py"
          }
    }
    stage('test') {
      steps {
        sh 'python tests.py'
      }
      post {
        always {
          junit 'test-reports/*.xml'
        }
      }
    }
  }
}
