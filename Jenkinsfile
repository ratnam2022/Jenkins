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
                    def tags = sh(script: 'git tag', returnStdout: true).trim()
                    def tagList = tags.split("\n").collect { 
                        it.trim() 
                    }
                    env.TAG_LIST = tagList.join("\n") 
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    def versionChoice = input(
                        id: 'versionChoice',
                        message: 'Select a version to deploy',
                        parameters: [choice(name: 'VERSION_NUMBER', choices: env.TAG_LIST, description: 'Please choose the version')]
                    )
                    env.SELECTED_VERSION = versionChoice
                }
                echo "Deploying the version: ${env.SELECTED_VERSION} to the ${params.ENVIRONMENT} environment."
            }
        }
    }
}
