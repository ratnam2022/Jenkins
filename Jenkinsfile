pipeline {
    agent any

    parameters {
        choice(name: 'ENVIRONMENT', choices: ['dev', 'test', 'prod'], description: 'Select the target environment')
        choice(name: 'APPLICATION_NAME', choices: ['app1', 'app2', 'app3'], description: 'Select the application to deploy')
        string(name: 'VERSION_NUMBER', choices: ['1', '2', '3'], description: 'Enter the version number') 
    }

    stages {
        stage('Deploy') {
            steps {
                echo "Deploying ${APPLICATION_NAME} version ${VERSION_NUMBER} to ${ENVIRONMENT} using ${DEPLOYMENT_TYPE} strategy"
                // Add your deployment steps here, using the selected parameters
            }
        }
    }
}
