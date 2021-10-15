node('slave1') {
	currentBuild.result = "SUCCESS"
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
	  currentBuild.result == 'FAILURE'
	    echo "Failure building"
	}
         stage ('post'){
         if ( currentBuild.result == 'SUCCESS') {
		   addBadge(icon: 'green.gif', text: 'Build Succeeded')
	 }
	if (currentBuild.result == 'FAILURE') {
		   addBadge(icon: 'red.gif', text: 'Build Failed')
	} 
     }
}
