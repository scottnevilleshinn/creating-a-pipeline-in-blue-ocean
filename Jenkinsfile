pipeline {
  agent {
    docker {
      args '-p 3000:3000'
      image 'docker.housescans.sfcoders.net:5000/base_python3.7:latest'
    }

  }
  stages {
    stage('Build') {
      steps {
        sh 'ls'
        sh 'env | sort'
      }
    }
    stage('Test') {
      environment {
        CI = 'true'
      }
      steps {
        sh './jenkins/scripts/test.sh'
      }
    }
    stage('Deliver') {
      steps {
        sh './jenkins/scripts/deliver.sh'
        input 'Finished using the web site? (Click "Proceed" to continue)'
        sh './jenkins/scripts/kill.sh'
      }
    }
  }
}