pipeline {
    agent any
    triggers {
        pollSCM("")
    }
    stages {
        stage("Prepare environment") {
            steps {
                checkout scm
            }
        }
        stage("Test") {
            steps {
                script {
                    echo "Test Successful"
                    
                }
            }
        }
        stage("Publish to Nexus"){
            steps {
                script{
                    echo "My branch is : ${env.BRANCH_NAME}"
                    if("${env.BRANCH_NAME}" == 'master'){
                        echo "Publishing ${env.BRANCH_NAME} to nexus"
                    }
                }
            }
        }
        stage("Cleanup") {
            steps{
                script {
                    deleteDir()
                    // after the push to nexus, we need to clean-up the docker image on the server
                }
            }
        }
    }
}
