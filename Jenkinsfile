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
    sh "git clone C:/Users/VJagarlamudi/Desktop/test/final/MedlineWebAutomation.git"
	sh 'git config --file=.MedlineWebAutomation/.gitmodules submodule.Core/FrameworkCore.url "C:/Users/VJagarlamudi/Desktop/test/final/FrameworkCore.git"'
	sh 'cd MedlineWebAutomation/'
	sh 'git submodule update --init'
	sh 'git remote update'
  
			 
      
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
