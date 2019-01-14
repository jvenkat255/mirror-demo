pipeline {
	agent { label 'ATG'}
	options { 
    skipDefaultCheckout()
    disableConcurrentBuilds()
   }
  
	 //String cron_string = BRANCH_NAME == "demo" ? ' */1 * * *' : ''
	
  //triggers { cron(cron_string) }
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
	    triggers {
    cron(env.BRANCH_NAME == 'demo' ? '*/1 * * *' : '')
  }
    }
	  stage('test') {
      steps {
        bat "gradle clean test"
      }
    }
	
  }
}
