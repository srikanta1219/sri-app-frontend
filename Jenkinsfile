pipeline {
    agent any
	

 stages {
      stage('checkout') {
           steps {
             
                git branch: 'master', url: 'https://github.com/srikanta1219/sri-app-frontend.git'
             
          }
        }
       

  stage('Docker Build and Tag') {
           steps {
              
                sh 'docker build -t srifrontend:latest .' 
                sh 'docker tag srifrontend srikanta1219/srifrontend:$BUILD_NUMBER'
               
          }
        }
  stage('Publish image to Docker Hub') {
            steps {
        withDockerRegistry([ credentialsId: "DockerHub", url: "" ]) {
           sh  'docker push srikanta1219/srifrontend:$BUILD_NUMBER' 
		}
                  
          }
        }
		
    }
}