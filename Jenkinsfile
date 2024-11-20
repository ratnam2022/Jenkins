def envList
def dockerId
node {
    envList = "defaultValue\n" + sh (script: 'pwd', returnStdout: true).trim()
}
pipeline {
    agent any
    parameters {
        choice(choices: "${envList}", name: 'DEPLOYMENT_ENVIRONMENT', description: 'please choose the environment you want to deploy?')
        booleanParam(name: 'SECURITY_SCAN',defaultValue: false, description: 'container vulnerability scan')
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
