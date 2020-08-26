pipeline {
    agent any
    	tools {
		maven "maven-container"
    }
    stages {
        stage('build') {
            steps {
                sh 'mvn clean package'
            }
        }
    }
    post {
        success {
            script {
                if ("${env.BRANCH_NAME}" == 'master')
                    discordSend description: "Success ${currentBuild.displayName}\n${currentBuild.absoluteUrl}", 
                        footer: "commit : ${env.GIT_COMMIT}", image: '', link: '', result: 'SUCCESS', thumbnail: '',
                        title: "${env.JOB_NAME} | Antoine", 
                        webhookURL: 'https://discordapp.com/api/webhooks/747819422705778738/dHWPHidlNLpiiKftWU84__Ss2LAkws77Swfdk5OWs22qla3hlI1B4zywW8ROg4nAwjRM'
            }
        }
        failure {
            discordSend description: "Failure ${currentBuild.displayName}\n${currentBuild.absoluteUrl}", 
                footer: "branch : ${env.BRANCH_NAME}\ncommit : ${env.GIT_COMMIT}", image: '', link: '', result: 'FAILURE', thumbnail: '',
               title: "${env.JOB_NAME} | Antoine", 
                 webhookURL: 'https://discordapp.com/api/webhooks/747819422705778738/dHWPHidlNLpiiKftWU84__Ss2LAkws77Swfdk5OWs22qla3hlI1B4zywW8ROg4nAwjRM'
        }
    }
}