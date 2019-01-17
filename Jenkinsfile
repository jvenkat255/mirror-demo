pipeline {
	agent { label 'ATG'}
	//triggers{ cron('H/15 * * * *') }
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
        git clone C:/Users/VJagarlamudi/Desktop/test/final/MedlineWebAutomation.git
	git config --file=./MedlineWebAutomation/.gitmodules submodule.Core/FrameworkCore.url "C:/Users/VJagarlamudi/Desktop/test/final/FrameworkCore.git"
	cd MedlineWebAutomation/
	git submodule update --init
	git remote update
      checkout(doGenerateSubmoduleConfigurations: false, extensions: [[$class: 'SubmoduleOption', disableSubmodules: true, parentCredentials: true, recursiveSubmodules: false, reference: '', trackingSubmodules: true]], submoduleCfg: [], userRemoteConfigs: [[url: 'C:/Users/VJagarlamudi/Desktop/test/final/MedlineWebAutomation.git']]])
			}  
      
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
