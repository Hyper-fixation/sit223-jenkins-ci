pipeline {
  agent any

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
