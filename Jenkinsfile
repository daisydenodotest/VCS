pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {

                bat 'rmdir /S /Q C:\Program Files\Jenkins\workspace\github_diff_1'
                
                // 拉取 GitHub 上的代码
                bat 'git clone https://github.com/daisydenodotest/VCS.git .'
            }
        }
        
        stage('Generate Diff') {
            steps {
                // 生成差异文件
                script {
                    def previousCommit = bat(script: 'git rev-parse HEAD^', returnStdout: true).trim()
                    def currentCommit = bat(script: 'git rev-parse HEAD', returnStdout: true).trim()
                    def diffOutput = bat(script: "git diff ${previousCommit} ${currentCommit}", returnStdout: true).trim()
                    echo "差異內容："
                    echo diffOutput
                }
            }
        }
    }
}
