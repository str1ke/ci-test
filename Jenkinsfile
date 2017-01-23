#!/usr/bin/env groovy

def projectProperties = [
    [$class: 'BuildDiscarderProperty',strategy: [$class: 'LogRotator', numToKeepStr: '5']],
]

properties(projectProperties)

try {
    stage('Checkout source') {
        checkout scm
    }

    stage('Build site') {
        timeout(60) {
            #
        }
    }

    /* The Jenkins which deploys doesn't use multibranch or GitHub Org Folders
     */
    if (env.BRANCH_NAME == null) {
        stage('Deploy site') {
            #
        }
    }
}
catch (exc) {
    echo "Caught: ${exc}"

    String recipient = 'str2ke@gmail.com'

    mail subject: "${env.JOB_NAME} (${env.BUILD_NUMBER}) failed",
            body: "It appears that ${env.BUILD_URL} is failing, somebody should do something about that",
              to: recipient,
         replyTo: recipient,
            from: 'noreply@jenkins'
}
