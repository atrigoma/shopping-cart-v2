pipeline {
   agent any

   parameters {
      booleanParam ( name: 'RUN_INTEGRATION_TESTS', defaultValue: true)
   }

   stages{
   	stage ('Test'){
	   parallel {
	      stage('Unit Test'){
	         steps {
  	            echo 'Executing Unit Test...'
		 }
	      }
	      stage('Integration Test'){
	         when {
		    expression {params.RUN_INTEGRATION_TESTS}
		 }
		 steps{
	            echo 'Executin Integration Test...'
		 }
	      }
	   }

	}
   }


}

