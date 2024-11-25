pipeline {
    agent any
    parameters {
        choice(name: 'ENVIRONMENT', choices: ['dev', 'uat','engg','prod'], description: 'Please choose the environment you want to deploy')
        choice(name: 'APPLICATION_NAME', choices: ['kinisi-ui', 'kinisi-app', 'kinisi-devops'], description: 'Select the application to deploy')
    }
    stages {
        stage('Get Tags') {
            steps {
                script {
                    // def tags = sh(script: 'git tag', returnStdout: true).trim()
                    sh """
                         #!/bin/bash
                        tags=\$(git tag)
                        echo "TAGS=$tags"
                    """
                    def filteredTags = tags.split("\n").findAll { 
                        it.startsWith("${params.ENVIRONMENT}/") 
                    }.collect { 
                        // Extract the version number from the tag
                        it.split("/")[1]  
                    }
                    env.FILTERED_TAG_LIST = filteredTags.join("\n") 
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    def versionChoice = input(
                        id: 'versionChoice',
                        message: 'Select a version to deploy',
                        parameters: [choice(name: 'VERSION_NUMBER', choices: env.FILTERED_TAG_LIST, description: 'Please choose the version')]
                    )
                    env.SELECTED_VERSION = versionChoice
                }
                echo "Deploying the version: ${env.SELECTED_VERSION} to the ${params.ENVIRONMENT} environment."
            }
        }
    }
}
