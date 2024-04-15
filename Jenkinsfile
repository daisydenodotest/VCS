pipeline {
    agent any
    
    stages {
        stage('Get Diff') {
            steps {
                script {
                    // 使用 PowerShell 获取当前分支的最新提交和前一个提交的 SHA
                    def currentCommit = bat(script: 'powershell -command "(git rev-parse HEAD)"', returnStdout: true).trim()
                    def previousCommit = bat(script: 'powershell -command "(git rev-parse HEAD^)"', returnStdout: true).trim()
                    
                    // 使用 PowerShell 比较两个提交之间的差异并输出到 Jenkins 构建日志中
                    def diffOutput = bat(script: "powershell -command \"(git diff ${previousCommit} ${currentCommit})\"", returnStdout: true).trim()
                    echo "差异内容："
                    echo diffOutput
                }
            }
        }
    }
}
