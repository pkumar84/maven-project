pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building First time and Hello world to jenkins..'
                sh 'mvn clean package'
            }
            post {
                echo 'Now Archiving...'
                achiveArtifacts artifacts: '**/target/*war'
            }
        }

    }
}