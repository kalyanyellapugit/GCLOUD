pipeline {
    agent any

    environment {
    SVC_ACCOUNT_KEY = credentials('Jenkins-secret')
  }
     
    stages {
      	stage('Set creds') {
            steps {
              
                sh 'echo $SVC_ACCOUNT_KEY | base64 -d > ./jenkins.json'
		        sh 'pwd'
                       
               
            }
        }

	
	stage('Auth-Project') {
	 steps {
    
        sh 'gcloud auth activate-service-account jenkins1@kalyanproject-dev.iam.gserviceaccount.com --key-file=jenkins.json'
    }
    }
	
 	 
	stage('Create Instance') {
	 steps {
    
    sh 'gcloud compute instances create test1 --zone=us-central1-a --tags=http-server --scopes=storage-ro --metadata-from-file=startup-script=./startupscript.sh'
      
    }
    }

    stage('Instance list') {
	 steps {
    
    sh 'gcloud compute instances list'
        
    }
    }
    
    
   }
}
