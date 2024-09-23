pipeline {

    agent any

    environment {
        MY_EMAIL = 'mbpool96@gmail.com'
    }

    stages {

        stage('Build') {
            steps {
                script {
                    echo "Building the code using Maven. Code is compiled and artifacts are generated..."
                    echo "Tool Used: Maven"
                    bat '''
                        echo Building the code using Maven. Code is compiled and artifacts are generated... > build.log
                        echo Tool Used: Maven >> build.log
                    '''
                }
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                script {
                    echo "Running the unit and integration tests..."
                    echo "Tool for Unit tests: JUnit"
                    echo "Tool for Integration tests: Selenium"
                    bat '''
                        echo Running the unit and integration tests... > unit_integration_tests.log
                        echo Tool for Unit tests: JUnit >> unit_integration_tests.log
                        echo Tool for Integration tests: Selenium >> unit_integration_tests.log
                    '''
                }
            }
            post {
                success {
                    emailext(
                        to: "$MY_EMAIL",
                        subject: "Jenkins Pipeline: Unit/Integration Tests Success",
                        body: "Unit and Integration Tests have passed.",
                        attachmentsPattern: 'unit_integration_tests.log'
                    )
                }
                failure {
                    emailext(
                        to: "$MY_EMAIL",
                        subject: "Jenkins Pipeline: Unit/Integration Tests Failed",
                        body: "Unit and Integration Tests have failed. Check the attached logs for details.",
                        attachmentsPattern: 'unit_integration_tests.log'
                    )
                }
            }
        }

        stage('Code Analysis') {
            steps {
                script {
                    echo "Performing code analysis..."
                    echo "Tool Used: SonarQube"
                    bat '''
                        echo Performing code analysis... > code_analysis.log
                        echo Tool Used: SonarQube >> code_analysis.log
                    '''
                }
            }
        }

        stage('Security Scan') {
            steps {
                script {
                    echo "Running security scan..."
                    echo "Tool Used: SonarQube Security"
                    bat '''
                        echo Running security scan... > security_scan.log
                        echo Tool Used: SonarQube Security >> security_scan.log
                    '''
                }
            }
            post {
                success {
                    emailext(
                        to: "$MY_EMAIL",
                        subject: "Jenkins Pipeline: Security Scan Success",
                        body: "Security scan completed successfully.",
                        attachmentsPattern: 'security_scan.log'
                    )
                }
                failure {
                    emailext(
                        to: "$MY_EMAIL",
                        subject: "Jenkins Pipeline: Security Scan Failed",
                        body: "Security scan failed. Review the attached logs for vulnerabilities.",
                        attachmentsPattern: 'security_scan.log'
                    )
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                script {
                    echo "Deploying the application to staging environment..."
                    echo "Tool Used: AWS EC2 instance"
                    bat '''
                        echo Deploying the application to staging environment... > deploy_staging.log
                        echo Tool Used: AWS EC2 instance >> deploy_staging.log
                    '''
                }
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                script {
                    echo "Running integration tests on staging environment..."
                    echo "Tool Used: Selenium"
                    bat '''
                        echo Running integration tests on staging environment... > integration_tests_staging.log
                        echo Tool Used: Selenium >> integration_tests_staging.log
                    '''
                }
            }
            post {
                success {
                    emailext(
                        to: "$MY_EMAIL",
                        subject: "Jenkins Pipeline: Integration Tests on Staging Success",
                        body: "Integration Tests on Staging have passed.",
                        attachmentsPattern: 'integration_tests_staging.log'
                    )
                }
                failure {
                    emailext(
                        to: "$MY_EMAIL",
                        subject: "Jenkins Pipeline: Integration Tests on Staging Failed",
                        body: "Integration Tests on Staging have failed. Check the attached logs for details.",
                        attachmentsPattern: 'integration_tests_staging.log'
                    )
                }
            }
        }

        stage('Deploy to Production') {
            steps {
                script {
                    echo "Deploying the application to production environment..."
                    echo "Tool Used: AWS EC2 instance"
                    bat '''
                        echo Deploying the application to production environment... > deploy_production.log
                        echo Tool Used: AWS EC2 instance >> deploy_production.log
                    '''
                }
            }
        }
    }
}
