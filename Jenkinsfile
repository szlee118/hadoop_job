node {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    def scannerHome = tool 'SonarScanner';
    withSonarQubeEnv() {
      sh "${scannerHome}/bin/sonar-scanner"
    }
  }

  stage('Access File') { 
    def filePath = "${env.WORKSPACE}/WordCount.java" 
    sh "cat ${filePath}" 
  }
  
  stage('Trigger Dataproc') {
    build 'dataproc'
  }
}
