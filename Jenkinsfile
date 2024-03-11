pipeline {
       agent {
               label "ubuntu-slave"
 
       }
       stages {
              stage ("Pulling the code from SCM") {
                     steps {
		              git branch: 'main', url: 'https://github.com/tripti31573157/new_java_app.git'
			   
              		   }
 
    
                  }

      
       	     stage ("Build the code") {
                      steps {
                              sh 'sudo mvn dependency:purge-local-repository'
			      sh 'mvn clean package'	  
  
		      }

		   }

	     stage ("Create docker image") {
                      steps {
                              sh 'sudo docker build -t java-app:$BUILD_TAG  .'
                              sh 'sudo docker tag java-app:$BUILD_TAG tripti14/java-app:$BUILD_TAG' 

      
		      }


	     }
	     stage ("push on Docker-Hub") {
	             steps {
                             withCredentials([string(credentialsId: 'Docker_pass_ID', variable: 'docker_hub_pass_var')]) {
                                     sh 'sudo docker login -u tripti14 -p ${docker_hub_pass_var}'
				     sh 'sudo docker push tripti14/java-app:$BUILD_TAG'
                     }  


		     } 

              } 
	     stage ("Testing the Build") {
                               steps {
                                         sh 'sudo docker run -dit --name java-test$BUILD_TAG -p 8080-8085:8080 tripti14/java-app:$BUILD_TAG'
		    }  

	     }
             stage ("QAT Testing") {
                          steps {
			          sh 'curl --silent http://13.201.131.1:8080/java-web-app/'
	     }


	     }
	       
             
      }      
	       
              
       

}  
