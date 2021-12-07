pipeline {
   agent any
  stages {
    stage('build') {
      steps {
           echo "build ..."
        sh 'cat /etc/os-release'
      }
    }


   stage('testing') {
      steps {
          echo "testing ..."
        sh '''
          cat /etc/os-release
          ls
          apt-get update
          php --version
          composer --version
           '''
      }
    }

   stage('deploy') {
      steps {
           echo "testing ..."
        sh 'cat /etc/os-release'
      }
    }

  }
}
