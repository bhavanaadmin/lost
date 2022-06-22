pipeline{
 agent any
 stages{
   stage('checkout'){
    steps{
      checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'a2da1015-7f77-42df-b059-48dc13804c2e', url: 'git@github.com:bhavanaadmin/lost.git']]])
    }
   }
   stage('Build'){
    steps{
     sh 'docker build -t gcr.io/gj-playground/app:pink .'
    }
   }
   stage('push'){
    steps{
     sh 'gcloud auth activate-service-account sample@gj-playground.iam.gserviceaccount.com --key-file=json.txt'
     sh 'gcloud auth configure-docker'
     sh 'docker push gcr.io/gj-playground/app:pink'
    }
   }
 }
}
