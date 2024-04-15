pipeline {
    agent any
    
    stages {
        stage('Get Diff') {
            steps {
                script {
                    def currentCommit = bat(script: 'powershell -command \"git rev-parse HEAD\"', returnStdout: true).trim()
                    def previousCommit = bat(script: 'powershell -command \"git rev-parse HEAD^\"', returnStdout: true).trim()

                    echo currentCommit
                    echo previousCommit

                    def command = "powershell -command \"git diff ${previousCommit} ${currentCommit}\""

                    echo command 
                    def diffOutput = bat(script: command, returnStdout: true)

                    echo "diff content："
                    echo diffOutput
                }
            }
        }
    }
}
