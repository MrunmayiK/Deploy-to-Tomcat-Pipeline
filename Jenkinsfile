node{

  // def tomcatWeb = 'C:\\Program Files\\Apache Software Foundation\\Tomcat 8.5\\webapps'
   //def tomcatBin = 'C:\\Program Files\\Apache Software Foundation\\Tomcat 8.5\\bin'
   //def tomcatStatus = ''
   def mvnHome = tool name:'MAVEN_HOME', type:'maven'
   stage('SCM Checkout'){
     git 'https://github.com/MrunmayiK/Deploy-to-Tomcat-Pipeline.git'
   }
   stage('Build'){
      // Get maven home path
     // def mvnHome =  tool name: 'MAVEN_HOME', type: 'maven'   
      sh "${mvnHome}/bin/mvn package"
      }
/*   stage ('Stop Tomcat Server') {
               bat ''' @ECHO OFF
               wmic process list brief | find /i "tomcat" > NUL
               IF ERRORLEVEL 1 (
                    echo  Stopped
               ) ELSE (
               echo running
                  "${tomcatBin}\\shutdown.bat"
                  sleep(time:10,unit:"SECONDS") 
               )
'''
   }*/
   stage('Deploy to Tomcat'){
     sh "cp target\\Deploy-to-Tomcat-Pipeline.war \"${tomcatWeb}\\Deploy-to-Tomcat-Pipeline.war\""
   }
      stage ('Start Tomcat Server') {
         sleep(time:5,unit:"SECONDS") 
         bat "${tomcatBin}\\startup.bat"
         sleep(time:100,unit:"SECONDS")
   }
}
