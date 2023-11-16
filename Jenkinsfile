pipeline {
    agent any

    stages{
        stage("Pull Latest Image"){
            steps{
                sh "docker pull atttest/entireconfigurationinyamlimage"
            }
        }
        stage("Start Grid"){
            steps{
                sh "docker-compose up -d hub chrome firefox"
            }
        }
        stage("Run Test"){
            steps{
                sh "docker-compose up cucumbertestcases"
            }
        }
    }
    post{
        always{
            archiveArtifacts artifacts: 'testcaseoutputfolder/**'
            sh "docker-compose down"
        }
    }
}
