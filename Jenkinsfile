pipeline {
    agent any
     tools {
        maven 'localMaven'
    }
    stages {
        stage('Build') {
            steps {
                echo 'Building First time and Hello world to jenkins..'
                sh 'mvn -DskipTests clean package'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*war'
                }
            }
        }
        stage('Deploy to staging') {
             steps {
                
                 build job: 'deploy-to-staging'
             }   
        }
        stage('Deploy to Prod') {
             steps {
                  timeout(time: 5, unit: 'DAYS') {
                     input message : "Do you Approve ?"
                 }
                 build job: 'deploy-to-prod'
                 
             }
             post {
                 success {
                     echo 'Code Deployed to prod successfully'
                 }
                 failure {
                     echo 'Deployment failed to prod'
                 }
             }   
        }

    }
}