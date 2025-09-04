pipeline {
  agent any
  options {
    timestamps()
    disableConcurrentBuilds()
  }

  stages {
    stage('Build') {
      steps {
        echo 'Task: Compile and package the application artifact.'
        echo 'Tool: Maven'
      }
    }
    
    stage('Unit and Integration Tests') {
      steps {
        echo 'Task: Run unit tests and integration tests to validate functionality and component interactions.'
        echo 'Tool: JUnit (unit), Testcontainers (integration)'
      }
    }
    
    stage('Code Analysis') {
      steps {
        echo 'Task: Perform static code analysis to enforce standards and measure maintainability.'
        echo 'Tool: SonarQube'
      }
    }
    stage('Security Scan') {
      steps {
        echo 'Task: Scan source and dependencies for known vulnerabilities.'
        echo 'Tool: Snyk'
      }
    }
    stage('Deploy to Staging') {
      steps {
        echo 'Task: Deploy artifact to a staging environment.'
        echo 'Tool: Docker on AWS EC2'
      }
    }
    stage('Integration Tests on Staging') {
      steps {
        echo 'Task: Run integration and end-to-end tests against the staging environment.'
        echo 'Tool: Postman/Newman'
      }
    }
    stage('Deploy to Production') {
      steps {
        echo 'Task: Deploy the validated build to production.'
        echo 'Tool: Ansible'
      }
    }
  }
}
