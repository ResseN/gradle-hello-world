node('slave1') {
	def gradleHome = tool 'gradle4'
	status = "OK"
   try {
         stage ('Checkout'){
            checkout scm      
         }
         stage ('Build Gradle'){
           sh "${gradleHome}/bin/gradle clean build"
         }
	 stage ('unit-test'){
	   sh "${gradleHome}/bin/gradle test"
	   junit "build/test-results/junit-platform/*.xml"
	 }
// 	 stage ('func-test'){
// 		 parallel {
// 			 stage('one'){
// 			 	sh "test-data/int-test.shbuild/libs/oto-gradle-1.0.jar otoMato 'Hello Otomato!'"
// 			 }
// 			 stage('two'){
// 				sh "test-data/int-test.shbuild/libs/oto-gradle-1.0.jar ResseN 'Hello Ressen!'" 
// 			 }
// 			 stage('three'){
// 				sh "test-data/int-test.shbuild/libs/oto-gradle-1.0.jar yuRiy 'Hello Yuriy!'"
// 			 }
// 		 }
	     
// 	 }   
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
