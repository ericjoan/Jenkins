pipeline {
    agent any

    stages {
        stage('Scan') {
            steps {
                withSonarQubeEnv(installationName: 'SonarQubePruebas') {
                sh './mvnw clean org.sonarsource.scanner.maven:sonar-maven-plugin:3.9.021155:sonar'
                }
            }
        }
        stage("Quality Gate"){
            steps{
                timeout(time: 2, unit: 'MINUTES'){
                    waitForQualityGate abortPipeline: true
                }
            }
        }
    }
}
