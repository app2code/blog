pipeline {
   agent {label "linux-ubuntu"}
   tools {nodejs "nodejs"}
  stages {
    stage('build') {
      steps {
           echo "build ..."
        sh 'cat /etc/os-release'
       // sh 'sudo npm i -g npm'
        sh 'mv .env.example .env'
         sh "sed -i -e 's/DB_HOST=localhost/DB_HOST=staging/g' .env"
        sh "sed -i -e 's/DB_DATABASE=staging/DB_DATABASE=staging/g' .env"
    	sh "sed -i -e 's/DB_USERNAME=root/DB_USERNAME=root/g' .env"
    	sh "sed -i -e 's/DB_PASSWORD=pass/DB_PASSWORD=pass/g' .env"

        sh 'composer install -n --ignore-platform-reqs'
        sh 'node -v'
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
