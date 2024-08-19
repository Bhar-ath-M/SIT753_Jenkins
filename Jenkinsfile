pipeline {

    agent any

    environment {

        DIRECTORY_PATH = '/path/to/your/code'

        TESTING_ENVIRONMENT = 'TestEnv'

        PRODUCTION_ENVIRONMENT = 'BharathProd'

    }

    stages {

        stage('Build') {

            steps {

                echo "Fetch the source code from the directory path specified by the environment variable: ${env.DIRECTORY_PATH}"

                echo "Compile the code and generate any necessary artifacts"

            }

        }

        stage('Test') {

            steps {

                echo "Running unit tests"

                echo "Running integration tests"

            }

        }

        stage('Code Quality Check') {

            steps {

                echo "Check the quality of the code"

            }

        }

        stage('Deploy') {

            steps {

                echo "Deploy the application to a testing environment specified by the environment variable: ${env.TESTING_ENVIRONMENT}"

            }

        }

        stage('Approval') {

            steps {

                echo "Waiting for manual approval"

                sleep(time: 10, unit: 'SECONDS')

            }

        }

        stage('Deploy to Production') {

            steps {

                echo "Deploy the code to the production environment using the environment variable: ${env.PRODUCTION_ENVIRONMENT}"

            }

        }

    }

}

 