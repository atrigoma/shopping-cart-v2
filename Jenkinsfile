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
		    sh './mvnw test -D testGroups=unit'
		 }
	      }
	      stage('Integration Test'){
	         when {
		    expression {params.RUN_INTEGRATION_TESTS}
		 }
		 steps{
	            echo 'Executin Integration Test...'
		    sh './mvnw test -D testGroups=integration'
		 }
	      }
	   }

	}
        stage ('Build'){
	   steps{
	      echo 'Executing build...'
	      script {
	         try {

	            sh './mvnw package -D skipTests'
	         }
	         catch (ex) {
	            echo 'Error while build the JAR'
		    throw ex
	         }
               }
	   }
	}
   }


}

