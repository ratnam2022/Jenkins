def verList
node {
    verList = "None\n" + sh (script: 'git branch -r', returnStdout: true).trim()
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
