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

	     stage ("Testing the build") {
                      steps {
                              sh 'sudo docker build -t java-app:$BUILD_TAG  .'

		      }


	     }
	     stage ("push on Docker") {
	             steps {
                             sh 'docker push [image-name]

		     } 

              }

	       
             
      }      
	       
              
       

}
