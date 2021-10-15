node('slave1') {
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
	    echo "Failure building"
	}
         stage ('post'){
              if ( currentBuild.result == 'SUCCESS') {
		      echo success
              }
              if (currentBuild.result == 'FAILURE') {
		      echo Fail
              }
         }
}
