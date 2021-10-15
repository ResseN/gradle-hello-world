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
                addErrorBadge id: 'ok', text: 'Build OK'
              }
              if (currentBuild.result == 'FAILURE') {
                addErrorBadge id: 'None', text: 'Build fail')
               }
         }
}
