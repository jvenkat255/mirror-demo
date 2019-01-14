pipeline {
	agent { label 'ATG'}
	options { 
    skipDefaultCheckout()
    disableConcurrentBuilds()
   }
  

  stages {
    stage('Clear workspace') {
      steps {
        cleanWs()
      }
    }  
    stage('Source Checkout') {
      steps {
        checkout([$class: 'GitSCM', branches: [[name: '*/$BRANCH_NAME']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'jvenkat255', url: 'git@github.com:jvenkat255/mirror-demo.git']]])
        }
    }
	  stage('test') {
      steps {
        gradle clean test
      }
    }
  }
}
