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
                
            }
        }

stage('Login to Docker hub') {
           steps {
              
                sh 'sudo docker login --username=venkibiligere --password=venki@0897'
                sh 'sudo docker tag testwebapp:latest venkibiligere/tomcatimages:testweb'
          }
        }
     
  stage('Publish image to Docker Hub') {
          
            steps {
       	  sh  'sudo docker push venkibiligere/tomcatimages:testweb'  
        }                 
          
        }
stage('pull') {
            steps {
                sh 'sudo docker pull venkibiligere/tomcatimages:testweb'
            }
        }     
      stage('Run Docker container on Jenkins Agent') {
             
            steps 
	      {
                sh "sudo docker run -d -p 8004:8080 venkibiligere/tomcatimages:testweb"
             }
        }
 
    }
	}
