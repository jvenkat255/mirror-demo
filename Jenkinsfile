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
        checkout([$class: 'GitSCM', branches: [[name: 'demo']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'jvenkat255', url: 'git@github.com:jvenkat255/mirror-demo.git']]])
        }
    }
	  stage('test') {
      steps {
        bat "gradle clean test"
      }
    }
	  
	  stage('cronjob') {
      steps {
        bat "*/01 * * *"
      }
    }
  }
}
