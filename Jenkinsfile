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
    def filePath1 = "${env.WORKSPACE}/WordCount.java" 
    sh "cat ${filePath1}" 
    def filePath2 = "${env.WORKSPACE}/WordCount.java" 
    sh "cat ${filePath2}" 
  }
  
  stage('Trigger Dataproc') {
    build 'dataproc'
  }
}
