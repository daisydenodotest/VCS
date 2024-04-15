pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                // 拉取 GitHub 上的代碼
                git credentialsId: 'jenkins_trigger_github', url: 'https://github.com/daisydenodotest/VCS.git'
            }
        }
        
        stage('Compare Versions') {
            steps {
                // 比較不同版本之間的差異並輸出到日誌
                script {
                    def diffOutput = sh(script: 'git log -p -1', returnStdout: true).trim()
                    echo "版本差異內容："
                    echo diffOutput
                }
            }
        }
    }
}
