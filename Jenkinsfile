node{
   stage('SCM Checkout'){
     git 'https://github.com/rekikamine/testpipeline-.git'
   }
   stage('Compile-Package'){
    
    withMaven(jdk: 'java8', maven: 'maven3', tempBinDir: '') {
 
      // Run the maven build
      bat "mvn clean install package"}
      }
   stage('SonarQube analysis code Quality') {
    // requires SonarQube Scanner 2.8+
    def scannerHome = tool 'sonar_Scanner';
    withSonarQubeEnv('sonarQuabe') {
      bat "${scannerHome}/bin/sonar-scanner.bat -e -Dsonar.projectName=qualite-code -Dsonar.projectVersion=1.4 -Dsonar.projectKey=amine -Dsonar.sources=src/main/java -Dsonar.language=java"
    }
  }
     
   }
