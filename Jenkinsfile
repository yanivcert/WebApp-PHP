pipeline {
    agent any
    stages {
        stage('Build (CI)') {
            steps {
                 git (url: 'https://github.com/yanivcert/WebApp-PHP.git', 
                      branch: 'master', poll: true) 
                echo "Do we have a commit?"
                echo "${env.GIT_COMMIT}"         
            }
        }
        stage('Deploy to Azure (CD)') {
                steps {
                    azureWebAppPublish appName: 'jenkins27402-php', azureCredentialsId: 'mySp', 
                    publishType: 'file', resourceGroup: 'Jenkins'
                }
        }
    }
    post {
        success {
            archiveArtifacts '*.php'
        }
    } 
}
