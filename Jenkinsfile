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
                    achiveArtifacts artifacts: '**/target/*war'
                }
            }
        }

    }
}