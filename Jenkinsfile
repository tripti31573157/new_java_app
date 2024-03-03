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
                              sh 'sudo docker run -dit --name java_app -p 8080:8080 java-app:$BUILD_TAG'

		      }


	     }


	       
             
      }      
	       
              
       

}
