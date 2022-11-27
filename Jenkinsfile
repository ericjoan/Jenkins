pipeline {
    agent any
    stages {
        
        stage('SonarQube analysis') {
            steps {
                withSonarQubeEnv('SonarQubePruebas') {
                    sh "mvn clean verify sonar:sonar -Dsonar.login=2945e12ff20e03cb698e1d7b7a1bb57bde76fa8f"
                }
            }
        }
        stage("Quality gate") {
            steps {
                waitForQualityGate abortPipeline: true
            }
        }
    }
}
