pipeline{
 agent any
 stages{
   stage('gitclone'){
    steps{
      git 'https://github.com/shazforiot/nodeapp_test.git'
    }
   }
   stage('Build'){
    steps{
     sh 'docker build -t gcr.io/gj-playground/app:pink .'
    }
   }
   stage('push'){
    steps{
     sh 'docker push gcr.io/gj-playground/app:pink .'
    }
   }
 }
}
