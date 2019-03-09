node{
   stage('SCM Checkout'){
     git 'https://github.com/rekikamine/testpipeline-.git'
   }
   stage('Compile-Package'){
    
    withMaven(jdk: 'java8', maven: 'maven3', tempBinDir: '') {
 
      // Run the maven build
      bat "mvn clean install package"}
      }
     
   }
