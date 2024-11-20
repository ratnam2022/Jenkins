pipeline {
    agent any

    parameters {
        choice(name: 'ENVIRONMENT', choices: ['dev', 'test', 'prod'], description: 'Select the target environment')
        choice(name: 'APPLICATION_NAME', choices: ['app1', 'app2', 'app3'], description: 'Select the application to deploy')
        string(name: 'VERSION_NUMBER', choices: generateRandomVersions(), description: 'Select the version number') 
    }

    stages {
        stage('Deploy') {
            steps {
                echo "Deploying ${APPLICATION_NAME} version ${VERSION_NUMBER} to ${ENVIRONMENT}"
                // Add your deployment steps here, using the selected parameters
            }
        }
    }
}

def generateRandomVersions() {
    def random = new Random()
    def versions = []
    3.times {
        versions << random.nextInt(100) // Generate random numbers between 0 and 99
    }
    return versions.join('\n') // Return the versions as a newline-separated string for the choice parameter
}
