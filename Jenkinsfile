pipeline {
    agent any
    triggers {
        pollSCM '* * * * *'
    }
    environment {
        RESOURCE_GROUP = 'Jenkins'
        APP_NAME = 'jenkins27402-php'
    }
    stages {
        stage('Build (CI)') {
            steps {
                git poll:false, changelog:false, url: 'https://github.com/yanivcert/WebApp-PHP.git'        
            }
        }
        stage('Deploy to Azure (CD)') {
                steps {
                    azureWebAppPublish appName: ${env.APP_NAME}, azureCredentialsId: 'mySp', 
                    publishType: 'file', resourceGroup: ${env.RESOURCE_GROUP}
                }
        }
    }
    post {
        success {
            archiveArtifacts '*.*'
        }
    } 
}
