pipeline {
  agent any

  environment {
    PATH = "C:\\Program Files\\Docker\\Docker\\resources\\bin;${env.PATH}"
  }

  stages {
    stage('Clean and Clone Repo') {
      steps {
        cleanWs()
        bat 'git clone https://github.com/ranidess/2317_ISA2.git'
      }
    }
    stage('Build') {
      steps {
        dir('2317_ISA2'){
          bat 'docker build -t mca2317/2317_ISA2 -f Dockerfile .'
        }
      }
    }
    stage('Delete') {
      steps {
        bat 'docker rm -f 2317'
      }
    }
    stage('Running in Daemon mode') {
      steps {
        bat 'docker run -d --name 2317 mca2317/2317_ISA2'
      }
    }
  }
}
