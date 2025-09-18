pipeline {
	agent any

	environment {
		EMAIL_TO = 's221245018@deakin.edu.au, harleyjack96@gmail.com'
		EMAIL_FROM = 'harleyjack96@gmail.com'
	}
	
	stages {
		stage('Build') {
			steps {
				echo "Stage 1: Build - Compiling and packaging the code using Maven." 
			}
		}

		stage('Unit and Integration Tests') {
			steps {
				echo "Stage 2: Unit and Integration Tests – Running tests with JUnit (unit) and Testcontainers (integration)."
			}
			post {
				success {
					emailext(
						to: EMAIL_TO, from: EMAIL_FROM, attachLog: true, mimeType: 'text/html',
						subject: "[${env.JOB_NAME}] Unit & Integration Tests SUCCESS - Build #${env.BUILD_NUMBER}",
						body: """
		 					<p><b>Stage:</b> Unit & Integration Tests</p>
							<p><b>Status:</b> SUCCESS</p>
							<p>Job: ${env.JOB_NAME}<br/>Build: #${env.BUILD_NUMBER}</p>
							<p>Console log attached. Link: <a href="${env.BUILD_URL}">${env.BUILD_URL}</a></p>
		  				"""
					)
				}
				failure {
					emailext(
						to: EMAIL_TO, from: EMAIL_FROM, attachLog: true, mimeType: 'text/html',
						subject: "[${env.JOB_NAME}] Unit & Integration Tests FAILURE - Build #${env.BUILD_NUMBER}",
						body: """
		 					<p><b>Stage:</b> Unit & Integration Tests</p>
							<p><b>Status:</b> FAILURE</p>
							<p>Job: ${env.JOB_NAME}<br/>Build: #${env.BUILD_NUMBER}</p>
							<p>Console log attached. Link: <a href="${env.BUILD_URL}">${env.BUILD_URL}</a></p>
		  				"""
					)
				}
			}
		}

		stage('Code Analysis') {
			steps {
				echo "Stage 3: Code Analysis – Analysing code quality with SonarQube."
			}
		}

		stage('Security Scan') {
			steps {
				echo "Stage 4: Security Scan – Scanning for vulnerabilities using Snyk."
			}
			post {
				success {
					emailext(
						to: EMAIL_TO, from: EMAIL_FROM, attachLog: true, mimeType: 'text/html',
						subject: "[${env.JOB_NAME}] Security Scan SUCCESS - Build #${env.BUILD_NUMBER}",
						body: """
	 						<p><b>Stage:</b> Security Scan</p>
				            <p><b>Status:</b> SUCCESS</p>
			    	        <p>Job: ${env.JOB_NAME}<br/>Build: #${env.BUILD_NUMBER}</p>
			        	    <p>Console log attached. Link: <a href="${env.BUILD_URL}">${env.BUILD_URL}</a></p>
			   			"""
					)
				}
				failure {
					emailext(
						to: EMAIL_TO, from: EMAIL_FROM, attachLog: true, mimeType: 'text/html',
	        			subject: "[${env.JOB_NAME}] Security Scan FAILURE - Build #${env.BUILD_NUMBER}",
						body: """
	 						<p><b>Stage:</b> Security Scan</p>
            	  			<p><b>Status:</b> FAILURE</p>
			    	        <p>Job: ${env.JOB_NAME}<br/>Build: #${env.BUILD_NUMBER}</p>
			        	    <p>Console log attached. Link: <a href="${env.BUILD_URL}">${env.BUILD_URL}</a></p>
            			"""
					)
				}
			}
		}

		stage ('Deploy to Staging') {
			steps {
				echo "Stage 5: Deploy to Staging – Deploying application to AWS EC2 using Docker."
			}
		}

		stage ('Integration Tests on Staging') {
			steps {
				echo "Stage 6: Integration Tests on Staging – Running end-to-end tests with Postman/Newman."
			}
		}

		stage ('Deploy to Production') {
			steps {
				echo "Stage 7: Deploy to Production – Releasing the application to production using Ansible."
			}
		}
	}
}
