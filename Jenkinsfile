node('slave1') {
	status = "OK"
   try {
         stage ('Checkout'){
            checkout scm      
         }
         stage ('Build Gradle'){
           def gradleHome = tool 'gradle4'
           sh "${gradleHome}/bin/gradle build"
           }
   } 
  catch (ex) {
	  status == 'Wrong'
	    echo "Failure building"
	}
         stage ('post'){
         if ( status == 'OK') {
		   addBadge(icon: 'completed.gif', text: 'Build Succeeded')
	 }
	if ( status == 'Wrong') {
		   addBadge(icon: 'error.gif', text: 'Build Failed')
	} 
     }
}
