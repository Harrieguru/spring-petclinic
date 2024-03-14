pipeline {
    agent any

    triggers {
        cron('H */10 * * 4') 
    }

    stages {
        stage('Build') {
            steps {
                bat 'mvn clean install'
            }
        }

        stage('Code Coverage Report') {
            steps {
                bat 'mvn jacoco:prepare-agent test jacoco:report'
                archiveArtifacts artifacts: '**/target/site/jacoco/*, **/target/*.jar', fingerprint: true
            }
        }
    }
}
