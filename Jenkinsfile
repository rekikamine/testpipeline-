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
      bat "${scannerHome}/bin/sonar-scanner.bat -e -Dsonar.projectName=qualite-code -Dsonar.projectVersion=2.4 -Dsonar.projectKey=amine -Dsonar.sources=src/main/java -Dsonar.language=java"
    }
  }
   stage('publish to Nexus'){
  nexusPublisher nexusInstanceId: 'nexusrep', nexusRepositoryId: 'maven-releases', packages: [[$class: 'MavenPackage', mavenAssetList: [[classifier: '', extension: '', filePath: 'target\\gestion-2.7.jar']], mavenCoordinate: [artifactId: 'gestion', groupId: 'org.xxx', packaging: 'jar', version: '3.1']]]
   }
   stage('notification'){
      mail bcc: '', body: 'la nouvelle job via le script du Jenkins Pipeline effectes avec succés', cc: '', from: '', replyTo: '', subject: 'build avec succés', to: 'bilel.essid@imiddleware.fr '
   }
   }
