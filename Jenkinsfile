pipeline {
   agent any

   parameters {
      booleanParam ( name: 'RUN_INTEGRATION_TESTS', defaultValue: true)
   }

   stages{
   	stage ('Test'){
	   parallel {
	      stage('Unit Test'){
	         echo 'Executing Unit Test...'
	      }
	      stage('Integration Test'){
	         when {
		    expression {RUN_INTEGRATION_TESTS}
		 }
	         echo 'Executin Integration Test...'
	      }
	   }

	}
   }


}

