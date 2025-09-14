pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Compiling and packaging application...'
                // Example: Maven build
                sh 'mvn clean package'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests...'
                // Example: JUnit or Mocha
                sh 'mvn test'
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Running static code analysis...'
                // Example: SonarQube or Checkstyle
                sh 'mvn checkstyle:check || true'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Performing security scan...'
                // Example: OWASP Dependency-Check or Snyk
                sh 'dependency-check.sh --project MyApp --scan . || true'
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying application to staging server...'
                // Example: Copy to AWS EC2 / Docker container
                sh 'scp target/myapp.jar user@staging-server:/opt/apps/'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging environment...'
                // Example: Selenium or Postman tests
                sh 'mvn verify -Pstaging-tests || true'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying application to production server...'
                // Example: Copy to production server
                sh 'scp target/myapp.jar user@production-server:/opt/apps/'
            }
        }
    }
}
