pipeline{
    agent any
    environment {
       PATH = "$PATH:/opt/apache-maven-3.9.0/bin"
    }
     stages{
       stage('GetCode'){
          steps{
             git 'https://github.com/Vinod2309/01-maven-web-App.git'
        }
       }
      stage('Build'){
          steps{
             sh 'mvn clean package'
        }
      }
      stage('SonarQube analysis') {
//    def scannerhome = tool'sonarScanner 4.0';
        steps{
        withSonarQubeEnv('Sonar-Server-8.9.10') {
        // if you have confugured more than one global server connection, you //can specify its name
//        sh "${scannerHome}/bin/sonar-scanner"
          sh "mvn sonar:sonar"
       }
          }
          }

     }
}
