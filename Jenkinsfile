def verList
node {
    verList = "defaultValue\n" + sh (script: 'date', returnStdout: true).trim()
}
pipeline {
    agent any
    parameters {
        choice(choices: "${verList}", name: 'VERSION_NUMBER', description: 'please choose the environment you want to deploy?')
    }
    stages {
        stage('Deploy') {
            steps {
                echo "Deploying the Version: ${params.VERSION_NUMBER}"
            }
        }
    }
}
