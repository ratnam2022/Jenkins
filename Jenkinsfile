pipeline {
    agent any
    parameters { 
        activeChoiceParam(
            name: 'FILE_OPTION',
            choiceType: 'SINGLE_SELECT',
            description: 'Select an option from the file',
            groovyScript: '''
                def fileContents = readFile 'file.txt'
                def options = fileContents.split("\n")
                return options
            '''
        )
    }
    stages {
        stage('Use Selected Option') {
            steps {
                echo "Selected Option: ${params.FILE_OPTION}"
            }
        }
    }
}
