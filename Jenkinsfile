def verList
node {
    def branches = sh(script: 'git branch -r', returnStdout: true).trim()
    verList = "None\n" + branches.split("\n").collect { 
        it.replace('origin/', '').trim()  // Remove 'origin/' prefix
    }.join("\n")
}
pipeline {
    agent any
    parameters {
        choice(choices: ['dev', 'test', 'prod'], name: 'ENVIRONMENT', description: 'please choose the environment you want to deploy?')
        choice(choices: "${verList}", name: 'VERSION_NUMBER', description: 'please choose the version you want to deploy?')
    }
    stages {
        stage('Deploy') {
            steps {
                echo "Deploying the Version: ${params.VERSION_NUMBER} to tne ${params.Environment} environment."
            }
        }
    }
}
