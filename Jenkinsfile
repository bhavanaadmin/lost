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
   stage('gcpcreds'){
    steps{
      withCredentials([file(credentialsId: '825a75d9-49a9-435e-a516-edb542222851', variable: 'GC_KEY')]) {
    sh("gcloud auth activate-service-account --key-file=${GC_KEY}")
    sh("gcloud auth configure-docker")
}
    }
   }
   stage('push'){
    steps{
     sh 'docker push gcr.io/gj-playground/app:pink'
    }
   }
 }
}
