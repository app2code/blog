pipeline {
   agent {label "linux-ubuntu"}
  stages {
    stage('build') {
      steps {
           echo "build ..."
        sh 'cat /etc/os-release'
       // sh 'sudo npm i -g npm'
        sh 'mv .env.example .env'
        sh 'composer install -n --ignore-platform-reqs'
        sh 'npm install'
        sh 'npm run production'
        sh 'php artisan key:generate'
        sh 'php artisan migrate'
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

         sh 'vendor/bin/phpunit'
      }
    }

   stage('deploy') {
      steps {
          timestamps {
           echo "deploy ..."
        sh 'cat /etc/os-release'
          }
      }
    }

  }
}
