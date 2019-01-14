pipeline {
	agent { label 'ATG'}
	triggers{ cron('H/15 * * * *') }
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
	  stage('mirror') {
      steps {
        bat "git clone --mirror [[credentialsId: 'jvenkat255', url: 'https://github.com/jvenkat255/aws-java-sample.git']]
      }
    }
    stage('Source Checkout') {
      steps {
        checkout([$class: 'GitSCM', branches: [[name: 'demo']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'jvenkat255', url: 'git@github.com:jvenkat255/mirror-demo.git']]])
        }
	   // triggers {
    		//cron(env.BRANCH_NAME == 'demo' ? '*/1 * * *' : '')
	  //  }
    }
	  stage('test') {
      steps {
        bat "gradle clean test"
      }
    }
	
  }
}
