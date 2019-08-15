pipeline {
    agent any
    triggers {
        pollSCM '* * * * *'
    }
    stages {
        stage('Build (CI)') {
            steps {
                 git url: 'https://github.com/yanivcert/php-docs-hello-world.git'            
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
