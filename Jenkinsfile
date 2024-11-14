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
    def filePath = "${env.WORKSPACE}/var/jenkins_home/workspace/sonar-git-jenkins/WordCount.java" 
    // Display file content sh "cat ${filePath}" 
  }
  
  stage('Trigger Dataproc') {
    build 'dataproc'
  }
}
