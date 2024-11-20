pipeline {
    agent any
    parameters {
        activeChoiceParam(
            name: 'ENVIRONMENT',
            choiceType: 'SINGLE_SELECT',
            description: 'Select the deployment environment',
            groovyScript: '''
                // Simulate fetching environments from a dynamic source
                def environments = ['dev', 'test', 'staging', 'prod'] 

                // You can add logic here to filter or modify the environments list
                // based on conditions or external data.

                return environments 
            '''
        )
    }
    stages {
        stage('Deploy') {
            steps {
                echo "Deploying to: ${params.ENVIRONMENT}"
                // Your deployment steps here, using the selected environment
                // Example:
                if (params.ENVIRONMENT == 'prod') {
                    // Execute production deployment commands
                } else {
                    // Execute deployment commands for other environments
                }
            }
        }
    }
}
