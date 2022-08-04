pipeline {
    agent any	
	 
 stages {
      stage('checkout') {
           steps {             
                git branch: 'master', url: 'https://github.com/venkibiligere/hello-world-war.git'             
          }
        }       

  stage('Docker Build and Tag') {
           steps {  
		 
                sh 'sudo docker build -t testwebapp:latest .' 
                sh 'sudo docker tag testwebapp dockvenki/testwebapp:latest' 
            }
        }

stage('Login to Docker hub') {
           steps {
              
                sh 'sudo docker login --username=dockvenki --password=BS_venki@97'
          }
        }
     
  stage('Publish image to Docker Hub') {
          
            steps {
       	  sh  'sudo docker push dockvenki/testwebapp:latest'  
        }                 
          
        }     
      stage('Run Docker container on Jenkins Agent') {
             
            steps 
	      {
                sh "sudo docker run -d -p 8004:8080 dockvenki/testwebapp:latest"
             }
        }
 
    }
	}
