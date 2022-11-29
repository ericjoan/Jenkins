pipeline {
    agent any
    stages {
        
        stage('SonarQube analysis') {
            steps {
                withSonarQubeEnv('SonarQubePruebas') {
                    bat "mvn clean verify sonar:sonar"
                }
            }
        }
        stage("Quality gate") {
            steps {
                timeout(time: 2, unit: 'MINUTES'){
                    waitForQualityGate abortPipeline: true
                }
            }
        }
        post{
            failure{
                bat "chrome /incognito url"
                timeout(time: 5, unit: 'SECONDS'){
                    bat "taskkill /F /IM Chrome.exe"
                }
            }
        }
    }
}
