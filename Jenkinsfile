pipeline {
    agent any
     tools {
        maven 'M3'
    }
    stages {
        stage('Build') {
            steps {
                echo 'Building First time and Hello world to jenkins..'
                sh 'mvn clean package'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    achiveArtifacts artifacts: '**/target/*war'
                }
            }
        }

    }
}