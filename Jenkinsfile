node ('slave1'){
  stage ('checkout'){
  checkout scm
  }
  stage ('build'){
  def gradleHome = tool 'gradle4'
      // Run the maven build
  sh "${gradleHome}/bin/gradle build"
  }  
}
