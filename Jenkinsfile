pipeline {
    agent any
    parameters {
        choice(choices: ['origin', 'local'], name: 'ENVIRONMENT', description: 'Please choose the environment you want to deploy?')
    }
    stages {
        stage('Get Versions') {
            steps {
                script {
                    def branches = sh(script: 'git branch -a', returnStdout: true).trim()
                    def filteredBranches = branches.split("\n").findAll { 
                        it.contains("${params.ENVIRONMENT}/")  // Filter based on selected environment
                    }.collect { 
                        it.trim() 
                    }
                    env.FILTERED_BRANCHES = filteredBranches.join("\n")
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    def versionChoice = input(
                        id: 'versionChoice',
                        message: 'Select a version to deploy',
                        parameters: [choice(name: 'VERSION_NUMBER', choices: env.FILTERED_BRANCHES, description: 'Please choose the version')]
                    )
                    env.SELECTED_VERSION = versionChoice
                }
                echo "Deploying the version: ${env.SELECTED_VERSION} to the ${params.ENVIRONMENT} environment."
            }
        }
    }
}
