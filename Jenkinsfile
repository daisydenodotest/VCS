pipeline {
    agent any
    
    parameters {
        string(name: 'BRANCH', defaultValue: 'main', description: 'Branch to compare')
    }
    
    stages {
        stage('Checkout') {
            steps {
                // 拉取指定分支的代碼
                checkout([$class: 'GitSCM', branches: [[name: '*/' + params.BRANCH]], userRemoteConfigs: [[url: 'https://github.com/daisydenodotest/VCS.git']]])
            }
        }
        
        stage('Generate Diff') {
            steps {
                // 生成差異文件
                script {
                    def previousCommit = sh(script: 'git rev-parse HEAD^', returnStdout: true).trim()
                    def currentCommit = sh(script: 'git rev-parse HEAD', returnStdout: true).trim()
                    
                    echo "Previous commit: $previousCommit"
                    echo "Current commit: $currentCommit"
                    
                    bat "git diff $previousCommit $currentCommit > diff.txt"
                }
            }
        }
        
        stage('Save Diff File') {
            steps {
                // 將差異文件保存到指定位置
                archiveArtifacts artifacts: 'diff.txt', onlyIfSuccessful: true
            }
        }
    }
}
