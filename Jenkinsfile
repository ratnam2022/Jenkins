pipeline {
    agent any
    parameters {
        choice(name: 'ENVIRONMENT', choices: ['dev', 'uat','engg','prod'], description: 'Please choose the environment you want to deploy')
        choice(name: 'APPLICATION_NAME', choices: ['kinisi-ui', 'kinisi-app', 'kinisi-devops'], description: 'Select the application to deploy')
    }
    stages {
        stage('Get Versions') {
            steps {
                script {
                    def branches = sh(script: 'git branch -a', returnStdout: true).trim()
                    def filteredBranches = branches.split("\n").findAll { 
                        it.contains("${params.ENVIRONMENT}/")
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
