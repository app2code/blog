pipeline {
   agent {label "linux-ubuntu"}
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
