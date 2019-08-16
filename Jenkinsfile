pipeline {
    agent any
    stages {
        stage('Build (CI)') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']],
                         doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [],
                         userRemoteConfigs: [[url: 'https://github.com/yanivcert/WebApp-PHP']]]
                         )        
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
