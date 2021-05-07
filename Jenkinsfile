pipeline {

agent any

stages {
	 stage('Build') {
	  steps {
	   echo 'Building.'

	   	
	   }
	}
	 stage('Test') {
	  steps {
	        sh "chmod +x -R ${env.WORKSPACE}"
	   	sh './tests.sh'
	   }
	}
    }
    post {
        failure {
            echo 'Success'
            emailext attachLog: true,
                body: "Build failed.",
                recipientProviders: [developers(), requestor()],
                to: 'knowak242@gmail.com',
                subject: "Build failed in Jenkins"
        }
        success {
            echo 'Fail'
            emailext attachLog: true,
                body: "Build successfull.",
                recipientProviders: [developers(), requestor()],
                to: 'knowak242@gmail.com',
                subject: "Successful build in Jenkins"
        }
    }
}

