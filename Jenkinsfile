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
                    
                    def diffOutput = bat(script: 'powershell -command "git diff VCS/Jenkinsfile VCS/Jenkinsfile"', returnStdout: true).trim()

                    echo "diff content："
                    echo diffOutput
                }
            }
        }
    }
}
